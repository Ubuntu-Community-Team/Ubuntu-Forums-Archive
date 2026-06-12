---
title: "openssl decrypt using private key"
date: 2011-03-12
forum: Security
---

### Post by shoot2kill on 2011-03-12
Hi, I am having some problems decrypting a given string/file using openssl.

I have used the command:
```

openssl rsautl -decrypt -in ciphertext -out plaintext -inkey private.pem

```

but all I get is the following error:
```

RSA operation error
20518:error:0406506C:rsa routines:RSA_EAY_PRIVATE_DECRYPT:data greater than mod len:rsa_eay.c:506:

```

The ciphertext is a file conatining a string which looks to be in base64 format.
Once the command has been run, with the error, a file is created called plaintext but it looks to be empty.

---

### Post by shoot2kill on 2011-03-12
Problem solved!

```

$ openssl enc -in ciphertext -out binarytext -d -a
$ openssl rsautl -decrypt -in binarytext -out plaintext -inkey private.pem 

```

---

