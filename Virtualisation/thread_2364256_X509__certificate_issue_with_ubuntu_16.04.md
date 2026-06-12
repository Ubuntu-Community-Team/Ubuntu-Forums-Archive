---
title: "X509 : certificate issue with ubuntu 16.04"
date: 2017-06-20
forum: Virtualisation
---

### Post by coolsarath2002 on 2017-06-20
Hi All,
I am new Linux,I installed Ubuntu in VirtualBox in my windows,I initially had certificate issue which got resolved once i imported the cert from Windows.
Now I am able to access the internet from ubuntu

I installed docker following the below documentation
[https://docs.docker.com/engine/installation/linux/ubuntu/](https://docs.docker.com/engine/installation/linux/ubuntu/)

Now I am getting the below certificate issue

sudo docker pull jenkins
sudo: unable to resolve host 
Using default tag: latest
Pulling repository docker.io/library/jenkins
Error while pulling image: Get [https://index.docker.io/v1/repositories/library/jenkins/images:](https://index.docker.io/v1/repositories/library/jenkins/images:) x509: certificate signed by unknown authority

curl on index.docker.io
$ curl [https://index.docker.io](https://index.docker.io)
curl: (60) server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
More details here: [http://curl.haxx.se/docs/sslcerts.html](http://curl.haxx.se/docs/sslcerts.html)

$ curl [https://www.google.com](https://www.google.com)
curl: (60) server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: none
More details here: [http://curl.haxx.se/docs/sslcerts.html](http://curl.haxx.se/docs/sslcerts.html)



How do i resolve the certificate issue.I followed documentation to generate a new self signed certificate with no luck.

---

### Post by howefield on 2017-06-21
Thread moved to the "*Virtualisation*" forum.

---

### Post by #&amp;thj^% on 2017-06-21
See if this helps: [https://stackoverflow.com/questions/31205438/docker-on-windows-boot2docker-certificate-signed-by-unknown-authority-error](https://stackoverflow.com/questions/31205438/docker-on-windows-boot2docker-certificate-signed-by-unknown-authority-error)

This can/will be Caused by self issued certificate authority. you should be able to solve it by adding ".pem" file to /usr/local/share/ca-certificates/ and calling
Give this a shot first.
```
sudo update-ca-certificates
```
Tip:
PS:And I myself have found that pem file in folder ./share/ca-certificates MUST have extension .crt

---

