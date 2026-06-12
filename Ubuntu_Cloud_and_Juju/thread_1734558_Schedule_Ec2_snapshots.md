---
title: "Schedule Ec2 snapshots"
date: 2011-04-20
forum: Ubuntu Cloud and Juju
---

### Post by MSPdwalt on 2011-04-20
I managed to get ec2-api-tools installed on my instance 

(had to add multiverse and partner repos)

I'm struggling to get ```
ec2-create-snapshot
``` to work and I believe it's a certificate issue, I'm just not sure where to go from here.

I'm attempting to follow [these instructions]("https://help.ubuntu.com/community/EC2StartersGuide") except I don't know where to find my private key file.  

The cert appears to be the .pem file I reference when I ssh into the server (or am I wrong).  Any help would be appreciated.

Most blog postings I've read suggest having one instance as a "commander" that executes ec2 related commands on other instances, but I don't see these guys needing another instance.  Are the api tools mad because I'm trying to execute commands on the instance that they are running on?

---

### Post by kim0 on 2011-04-22
Hey there, You will probably enjoy this article
[http://aws.amazon.com/articles/1663?_encoding=UTF8&jiveRedirect=1](http://aws.amazon.com/articles/1663?_encoding=UTF8&jiveRedirect=1)
About best practices for backing up and snapshotting an instance data

---

### Post by MSPdwalt on 2011-04-22
Thanks Kim, great article....I'll defiantly use that as a reference for my next MySQL deployment.

Unfortunately I still can't get any of the ec2-api-tools commands to work.  Still having certificate/key issues.  Which is which? is the cert the .pem file I got from the Ec2 Key pair? If so what/where is the key?

---

### Post by MSPdwalt on 2011-04-26
This is what happens when I run the command (I think I have the keys right)

```

ubuntu@ip-10-116-157-235:~$ ec2-create-snapshot -K .ssh/authorized_keys -C fredkey.pem vol-ea908c82
Unexpected error:
org.codehaus.xfire.fault.XFireFault: General security error; nested exception is: 
	java.security.cert.CertificateParsingException: signed overrun, bytes = 918
	at org.codehaus.xfire.fault.XFireFault.createFault(XFireFault.java:89)
	at org.codehaus.xfire.client.Invocation.invoke(Invocation.java:83)
	at org.codehaus.xfire.client.Invocation.invoke(Invocation.java:114)
	at org.codehaus.xfire.client.Client.invoke(Client.java:336)
	at org.codehaus.xfire.client.XFireProxy.handleRequest(XFireProxy.java:77)
	at org.codehaus.xfire.client.XFireProxy.invoke(XFireProxy.java:57)
	at $Proxy12.createSnapshot(Unknown Source)
	at com.amazon.aes.webservices.client.Jec2.createSnapshot(Jec2.java:2561)
	at com.amazon.aes.webservices.client.cmd.CreateSnapshot.invokeOnline(CreateSnapshot.java:64)
	at com.amazon.aes.webservices.client.cmd.BaseCmd.invoke(BaseCmd.java:742)
	at com.amazon.aes.webservices.client.cmd.CreateSnapshot.main(CreateSnapshot.java:74)
Caused by: org.apache.ws.security.WSSecurityException: General security error; nested exception is: 
	java.security.cert.CertificateParsingException: signed overrun, bytes = 918
	at com.amazon.aes.webservices.client.CryptoProxy.getCertificates(CryptoProxy.java:76)
	at org.apache.ws.security.message.WSSecSignature.prepare(WSSecSignature.java:286)
	at com.amazon.aes.webservices.client.Jec2.signRequest(Jec2.java:231)
	at com.amazon.aes.webservices.client.Jec2.access$000(Jec2.java:58)
	at com.amazon.aes.webservices.client.Jec2$1.invoke(Jec2.java:143)
	at org.codehaus.xfire.handler.HandlerPipeline.invoke(HandlerPipeline.java:131)
	at org.codehaus.xfire.client.Invocation.invoke(Invocation.java:79)
	... 9 more
Caused by: java.security.cert.CertificateParsingException: signed overrun, bytes = 918
	at sun.security.x509.X509CertImpl.parse(X509CertImpl.java:1730)
	at sun.security.x509.X509CertImpl.<init>(X509CertImpl.java:196)
	at sun.security.provider.X509Factory.engineGenerateCertificate(X509Factory.java:118)
	at java.security.cert.CertificateFactory.generateCertificate(CertificateFactory.java:322)
	at com.amazon.aes.webservices.client.CryptoProxy.getCertByName(CryptoProxy.java:116)
	at com.amazon.aes.webservices.client.CryptoProxy.getCertificates(CryptoProxy.java:74)
	... 15 more

```

Does this mean anything to anyone?

---

### Post by MSPdwalt on 2011-04-26
So here's what I did wrong,

You need to Generate an X.509 certificate pair from the AWS website NOT the management console.  This has nothign to do with SSH keypairs. You go to account, then security credentials.

---

