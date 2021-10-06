# java-AESEncryptor
java AES 암호화 복호화

```C

  public class AESEncryptor {
	Logger log = Logger.getRootLogger();
	
	private static final byte[] key = "123456789".getBytes(StandardCharsets.UTF_8);
	
	private static final String ALGO = "AES";
	
	public static AESEncryptor instance = new AESEncryptor();
	
	 public String encrypt(String plainText) throws Exception {
	        return Base64.getEncoder().encodeToString(this.encrypt(plainText.getBytes(StandardCharsets.UTF_8)));
	    }
	
	    public String decrypt(String encText) throws Exception {
	        return new String(decrypt(Base64.getDecoder().decode(encText)), StandardCharsets.UTF_8);
	    }
	
	    private byte[] encrypt(byte[] plainText) throws Exception {
	        SecretKeySpec secretKey = new SecretKeySpec(key, ALGO);
	        Cipher cipher = Cipher.getInstance(ALGO);
	        cipher.init(Cipher.ENCRYPT_MODE, secretKey);
	
	        return cipher.doFinal(plainText);
	    }
	
	    private byte[] decrypt(byte[] cipherText) throws Exception {
	        SecretKeySpec secretKey = new SecretKeySpec(key, ALGO);
	        Cipher cipher = Cipher.getInstance(ALGO);
	        cipher.init(Cipher.DECRYPT_MODE, secretKey);
	
	        return cipher.doFinal(cipherText);
	    }
}

```
