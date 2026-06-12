---
title: "openssl base64 decrypt question"
date: 2010-05-06
forum: Security
---

### Post by methodtwo on 2010-05-06
Hi
I need to be able to decrypt data, like simple text files, that have been encrypted and base64 encoded with my public key.I need to use openssl
so i do:
```
$cat encrypted | openssl enc -base64 -d > ./answer.txt
```and i get exactly the same data as before the command was run.
Am i right in thinking that i need to decode before decrypting?
I tried decrypting, before i realized that i had to decode first,using this command:
```
$cat encrypted | openssl rsautl -decrypt -out answer.txt -inkey privatekey.pem
```and i got this error:
```
RSA operation error
15850:error:0406506C:rsa routines:RSA_EAY_PRIVATE_DECRYPT:data greater than mod len:/on10/build-nd/G10U4B0/usr/src/common/openssl/crypto/rsa/rsa_eay.c:393:
```I think my problems are related to base64 line length restrictions.So how do i get round base64 line length problems and base64 decode then decrypt using my privatekey?.I've looked on the openssl web site but i couldn't find anything about base64 line length restrictions and how that may effect decoding!.
Any help would be great.Thank you for your time
regards methodtwo

---

### Post by ninja123 on 2010-09-02
Hi,


Any success with your trials?

I am encountering the same problem.

Can you help me?

---

### Post by anomie on 2010-09-02
@ninja123: I'm replying to you, because you dug up a couple months old thread, and OP may or may not be monitoring it. 

Simply use the enc(1) options to decrypt and base64-decode in a single command. There is usually not a good reason to perform the two steps separately. 

```
$ openssl enc -in foo.cipher -out foo.clear -d -a
```

If that's not working, please describe *your* problem in more detail, and include (in code tags) any relevant error messages.

---

