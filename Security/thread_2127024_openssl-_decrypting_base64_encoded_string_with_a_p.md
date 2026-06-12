---
title: "openssl- decrypting base64 encoded string with a private key"
date: 2013-03-18
forum: Security
---

### Post by rolaluv on 2013-03-18
Hello,

I'm trying to decode an IV and a session key that are encrypted with my private key. They are padded using the openssl default, so I can use the following command:

   (1) openssl rsautl -decrypt -inkey mykey.pem -in binary_file -out output_file.txt  

However, the session key and the IV are base64 decrypted, so I have to decrypt them using the following command:

(2) openssl base64 -d -in input_file.txt -out output_file.txt

The output file contains an ASCII string, I belive, and I can't convert it to a binary file, which is required for command (1).

I tried converting the base64 strings directly to binary files by using the online converter (this allows me to save the output as binary files): [http://www.motobit.com/util/base64-decoder-encoder.asp](http://www.motobit.com/util/base64-decoder-encoder.asp)

But, the result is same as running cammand (2).

What should I do to run command (1)? Thanks!

---

