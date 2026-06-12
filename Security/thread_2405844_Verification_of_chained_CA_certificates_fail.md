---
title: "Verification of chained CA certificates fail"
date: 2018-11-12
forum: Security
---

### Post by May_Masters on 2018-11-12
I've created a root-CA an intermediate-CA and a leaf cert.
Afterwards I stacked the root-CA and inter-CA in fullchain.pem

But when I try to verify the leave-cert it fails with:


 ```
openssl verify -check_ss_sig -CAfile full-chain.pem client-net.cr

error 24 at 1 depth lookup: invalid CA certificate
error client-net.crt: verification failed


``` 
the files were created like this:

 ```
openssl genrsa -out root-ca.key 4096 

openssl req -x509 -new -nodes -extensions v3_ca -key root-ca.key -out root-ca.crt -subj "/CN=ROOT-CA/O=special.net" -sha512  -days 7300

openssl genrsa -out inter-ca.key 4096

openssl req -new -key inter-ca.key -out inter.csr -subj "/CN=INTER-CA/O=special.net" -sha512 -days 3650

openssl x509 -req -in inter.csr -CA root-ca.crt -CAkey root-ca.key -CAcreateserial -out inter-ca.crt -sha512 -days 3650

cat root-ca.crt inter-ca.crt >> full-chain.pem

openssl genrsa -out client-net.key 4096

openssl req -new -key client-net.key -out client-net.csr -subj "/CN=client.special.net/O=special.net" -sha512 -days 3650

openssl x509 -req -in client-net.csr -CA inter-ca.crt -CAkey inter-ca.key -CAcreateserial -out client-net.crt -sha512 -days 3650

``` Additionally a further check of the issuer/subject also shows that  the certs are linked correctly and the subject hash matches the issuer  hash of the former cert:
 ```
echo "root-ca.crt"
printf "issuer: " ; openssl x509 -noout -issuer_hash -in root-ca.crt
printf "subject: " ; openssl x509 -noout -subject_hash -in root-ca.crt
echo

echo "inter-ca.crt"
printf "issuer: " ; openssl x509 -noout -issuer_hash -in inter-ca.crt
printf "subject: " ; openssl x509 -noout -subject_hash -in inter-ca.crt
echo

echo "client-net.crt"
printf "issuer: " ; openssl x509 -noout -issuer_hash -in client-net.crt
printf "subject: " ; openssl x509 -noout -subject_hash -in client-net.crt

```
root-ca.crt
issuer: b9107d09
subject: b9107d09

inter-ca.crt
issuer: b9107d09
subject: c998e801

client-net.crt
issuer: c998e801
subject: 8255fd0b


still the verification fails ... no clue why.
Tested with OpenSSL 1.1.0g  2 Nov 2017 on Ubuntu-Server 18.04

---

