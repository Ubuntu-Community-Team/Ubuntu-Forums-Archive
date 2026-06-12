---
title: "Unable to connect Nixnote to Evernote server. Transport Exception."
date: 2012-02-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by donniezazen on 2012-02-21
I installed Nixnote 1.2, manually and from ppa. It is unable to connect to Evernote Server in both stances.

Thanks.

```
javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
```

```
javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
```

```
nixnote
QtJambiInternal.buildMetaData: Writer for property content takes a type which is incompatible with reader's return type.
org.apache.thrift.transport.TTransportException: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at org.apache.thrift.transport.THttpClient.flush(THttpClient.java:154)
	at com.evernote.edam.userstore.UserStore$Client.send_authenticate(UserStore.java:136)
	at com.evernote.edam.userstore.UserStore$Client.authenticate(UserStore.java:122)
	at cx.fbn.nevernote.threads.SyncRunner.enConnect(SyncRunner.java:1519)
	at cx.fbn.nevernote.NeverNote.remoteConnect(NeverNote.java:3402)
	at cx.fbn.nevernote.NeverNote.<init>(NeverNote.java:721)
	at cx.fbn.nevernote.NeverNote.main(NeverNote.java:807)
Caused by: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at sun.security.ssl.Alerts.getSSLException(Alerts.java:208)
	at sun.security.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1697)
	at sun.security.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1660)
	at sun.security.ssl.SSLSocketImpl.handleException(SSLSocketImpl.java:1643)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1224)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1201)
	at sun.net.www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:440)
	at sun.net.www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:185)
	at sun.net.www.protocol.https.HttpsURLConnectionImpl.connect(HttpsURLConnectionImpl.java:153)
	at org.apache.thrift.transport.THttpClient.flush(THttpClient.java:142)
	... 6 more
Caused by: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at sun.security.validator.PKIXValidator.<init>(PKIXValidator.java:75)
	at sun.security.validator.Validator.getInstance(Validator.java:178)
	at sun.security.ssl.X509TrustManagerImpl.getValidator(X509TrustManagerImpl.java:129)
	at sun.security.ssl.X509TrustManagerImpl.checkServerTrusted(X509TrustManagerImpl.java:225)
	at sun.security.ssl.X509TrustManagerImpl.checkServerTrusted(X509TrustManagerImpl.java:270)
	at sun.security.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1144)
	at sun.security.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:154)
	at sun.security.ssl.Handshaker.processLoop(Handshaker.java:609)
	at sun.security.ssl.Handshaker.process_record(Handshaker.java:545)
	at sun.security.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:945)
	at sun.security.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1190)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1217)
	... 11 more
Caused by: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at java.security.cert.PKIXParameters.setTrustAnchors(PKIXParameters.java:200)
	at java.security.cert.PKIXParameters.<init>(PKIXParameters.java:120)
	at java.security.cert.PKIXBuilderParameters.<init>(PKIXBuilderParameters.java:104)
	at sun.security.validator.PKIXValidator.<init>(PKIXValidator.java:73)
	... 22 more
org.apache.thrift.transport.TTransportException: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at org.apache.thrift.transport.THttpClient.flush(THttpClient.java:154)
	at com.evernote.edam.userstore.UserStore$Client.send_checkVersion(UserStore.java:97)
	at com.evernote.edam.userstore.UserStore$Client.checkVersion(UserStore.java:84)
	at cx.fbn.nevernote.threads.SyncRunner.enConnect(SyncRunner.java:1539)
	at cx.fbn.nevernote.NeverNote.remoteConnect(NeverNote.java:3402)
	at cx.fbn.nevernote.NeverNote.<init>(NeverNote.java:721)
	at cx.fbn.nevernote.NeverNote.main(NeverNote.java:807)
Caused by: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at sun.security.ssl.Alerts.getSSLException(Alerts.java:208)
	at sun.security.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1697)
	at sun.security.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1660)
	at sun.security.ssl.SSLSocketImpl.handleException(SSLSocketImpl.java:1643)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1224)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1201)
	at sun.net.www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:440)
	at sun.net.www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:185)
	at sun.net.www.protocol.https.HttpsURLConnectionImpl.connect(HttpsURLConnectionImpl.java:153)
	at org.apache.thrift.transport.THttpClient.flush(THttpClient.java:142)
	... 6 more
Caused by: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at sun.security.validator.PKIXValidator.<init>(PKIXValidator.java:75)
	at sun.security.validator.Validator.getInstance(Validator.java:178)
	at sun.security.ssl.X509TrustManagerImpl.getValidator(X509TrustManagerImpl.java:129)
	at sun.security.ssl.X509TrustManagerImpl.checkServerTrusted(X509TrustManagerImpl.java:225)
	at sun.security.ssl.X509TrustManagerImpl.checkServerTrusted(X509TrustManagerImpl.java:270)
	at sun.security.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1144)
	at sun.security.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:154)
	at sun.security.ssl.Handshaker.processLoop(Handshaker.java:609)
	at sun.security.ssl.Handshaker.process_record(Handshaker.java:545)
	at sun.security.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:945)
	at sun.security.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1190)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1217)
	... 11 more
Caused by: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at java.security.cert.PKIXParameters.setTrustAnchors(PKIXParameters.java:200)
	at java.security.cert.PKIXParameters.<init>(PKIXParameters.java:120)
	at java.security.cert.PKIXBuilderParameters.<init>(PKIXBuilderParameters.java:104)
	at sun.security.validator.PKIXValidator.<init>(PKIXValidator.java:73)
	... 22 more
Incomatible EDAM client protocol version
org.apache.thrift.transport.TTransportException: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at org.apache.thrift.transport.THttpClient.flush(THttpClient.java:154)
	at com.evernote.edam.userstore.UserStore$Client.send_getUser(UserStore.java:220)
	at com.evernote.edam.userstore.UserStore$Client.getUser(UserStore.java:209)
	at cx.fbn.nevernote.threads.SyncRunner.enConnect(SyncRunner.java:1577)
	at cx.fbn.nevernote.NeverNote.remoteConnect(NeverNote.java:3402)
	at cx.fbn.nevernote.NeverNote.<init>(NeverNote.java:721)
	at cx.fbn.nevernote.NeverNote.main(NeverNote.java:807)
Caused by: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at sun.security.ssl.Alerts.getSSLException(Alerts.java:208)
	at sun.security.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1697)
	at sun.security.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1660)
	at sun.security.ssl.SSLSocketImpl.handleException(SSLSocketImpl.java:1643)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1224)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1201)
	at sun.net.www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:440)
	at sun.net.www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:185)
	at sun.net.www.protocol.https.HttpsURLConnectionImpl.connect(HttpsURLConnectionImpl.java:153)
	at org.apache.thrift.transport.THttpClient.flush(THttpClient.java:142)
	... 6 more
Caused by: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at sun.security.validator.PKIXValidator.<init>(PKIXValidator.java:75)
	at sun.security.validator.Validator.getInstance(Validator.java:178)
	at sun.security.ssl.X509TrustManagerImpl.getValidator(X509TrustManagerImpl.java:129)
	at sun.security.ssl.X509TrustManagerImpl.checkServerTrusted(X509TrustManagerImpl.java:225)
	at sun.security.ssl.X509TrustManagerImpl.checkServerTrusted(X509TrustManagerImpl.java:270)
	at sun.security.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1144)
	at sun.security.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:154)
	at sun.security.ssl.Handshaker.processLoop(Handshaker.java:609)
	at sun.security.ssl.Handshaker.process_record(Handshaker.java:545)
	at sun.security.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:945)
	at sun.security.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1190)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1217)
	... 11 more
Caused by: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at java.security.cert.PKIXParameters.setTrustAnchors(PKIXParameters.java:200)
	at java.security.cert.PKIXParameters.<init>(PKIXParameters.java:120)
	at java.security.cert.PKIXBuilderParameters.<init>(PKIXBuilderParameters.java:104)
	at sun.security.validator.PKIXValidator.<init>(PKIXValidator.java:73)
	... 22 more
org.apache.thrift.transport.TTransportException: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at org.apache.thrift.transport.THttpClient.flush(THttpClient.java:154)
	at com.evernote.edam.userstore.UserStore$Client.send_authenticate(UserStore.java:136)
	at com.evernote.edam.userstore.UserStore$Client.authenticate(UserStore.java:122)
	at cx.fbn.nevernote.threads.SyncRunner.enConnect(SyncRunner.java:1519)
	at cx.fbn.nevernote.NeverNote.remoteConnect(NeverNote.java:3422)
	at cx.fbn.nevernote.NeverNote.<init>(NeverNote.java:721)
	at cx.fbn.nevernote.NeverNote.main(NeverNote.java:807)
Caused by: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at sun.security.ssl.Alerts.getSSLException(Alerts.java:208)
	at sun.security.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1697)
	at sun.security.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1660)
	at sun.security.ssl.SSLSocketImpl.handleException(SSLSocketImpl.java:1643)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1224)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1201)
	at sun.net.www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:440)
	at sun.net.www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:185)
	at sun.net.www.protocol.https.HttpsURLConnectionImpl.connect(HttpsURLConnectionImpl.java:153)
	at org.apache.thrift.transport.THttpClient.flush(THttpClient.java:142)
	... 6 more
Caused by: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at sun.security.validator.PKIXValidator.<init>(PKIXValidator.java:75)
	at sun.security.validator.Validator.getInstance(Validator.java:178)
	at sun.security.ssl.X509TrustManagerImpl.getValidator(X509TrustManagerImpl.java:129)
	at sun.security.ssl.X509TrustManagerImpl.checkServerTrusted(X509TrustManagerImpl.java:225)
	at sun.security.ssl.X509TrustManagerImpl.checkServerTrusted(X509TrustManagerImpl.java:270)
	at sun.security.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1144)
	at sun.security.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:154)
	at sun.security.ssl.Handshaker.processLoop(Handshaker.java:609)
	at sun.security.ssl.Handshaker.process_record(Handshaker.java:545)
	at sun.security.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:945)
	at sun.security.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1190)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1217)
	... 11 more
Caused by: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at java.security.cert.PKIXParameters.setTrustAnchors(PKIXParameters.java:200)
	at java.security.cert.PKIXParameters.<init>(PKIXParameters.java:120)
	at java.security.cert.PKIXBuilderParameters.<init>(PKIXBuilderParameters.java:104)
	at sun.security.validator.PKIXValidator.<init>(PKIXValidator.java:73)
	... 22 more
org.apache.thrift.transport.TTransportException: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at org.apache.thrift.transport.THttpClient.flush(THttpClient.java:154)
	at com.evernote.edam.userstore.UserStore$Client.send_checkVersion(UserStore.java:97)
	at com.evernote.edam.userstore.UserStore$Client.checkVersion(UserStore.java:84)
	at cx.fbn.nevernote.threads.SyncRunner.enConnect(SyncRunner.java:1539)
	at cx.fbn.nevernote.NeverNote.remoteConnect(NeverNote.java:3422)
	at cx.fbn.nevernote.NeverNote.<init>(NeverNote.java:721)
	at cx.fbn.nevernote.NeverNote.main(NeverNote.java:807)
Caused by: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at sun.security.ssl.Alerts.getSSLException(Alerts.java:208)
	at sun.security.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1697)
	at sun.security.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1660)
	at sun.security.ssl.SSLSocketImpl.handleException(SSLSocketImpl.java:1643)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1224)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1201)
	at sun.net.www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:440)
	at sun.net.www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:185)
	at sun.net.www.protocol.https.HttpsURLConnectionImpl.connect(HttpsURLConnectionImpl.java:153)
	at org.apache.thrift.transport.THttpClient.flush(THttpClient.java:142)
	... 6 more
Caused by: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at sun.security.validator.PKIXValidator.<init>(PKIXValidator.java:75)
	at sun.security.validator.Validator.getInstance(Validator.java:178)
	at sun.security.ssl.X509TrustManagerImpl.getValidator(X509TrustManagerImpl.java:129)
	at sun.security.ssl.X509TrustManagerImpl.checkServerTrusted(X509TrustManagerImpl.java:225)
	at sun.security.ssl.X509TrustManagerImpl.checkServerTrusted(X509TrustManagerImpl.java:270)
	at sun.security.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1144)
	at sun.security.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:154)
	at sun.security.ssl.Handshaker.processLoop(Handshaker.java:609)
	at sun.security.ssl.Handshaker.process_record(Handshaker.java:545)
	at sun.security.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:945)
	at sun.security.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1190)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1217)
	... 11 more
Caused by: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at java.security.cert.PKIXParameters.setTrustAnchors(PKIXParameters.java:200)
	at java.security.cert.PKIXParameters.<init>(PKIXParameters.java:120)
	at java.security.cert.PKIXBuilderParameters.<init>(PKIXBuilderParameters.java:104)
	at sun.security.validator.PKIXValidator.<init>(PKIXValidator.java:73)
	... 22 more
Incomatible EDAM client protocol version
org.apache.thrift.transport.TTransportException: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at org.apache.thrift.transport.THttpClient.flush(THttpClient.java:154)
	at com.evernote.edam.userstore.UserStore$Client.send_getUser(UserStore.java:220)
	at com.evernote.edam.userstore.UserStore$Client.getUser(UserStore.java:209)
	at cx.fbn.nevernote.threads.SyncRunner.enConnect(SyncRunner.java:1577)
	at cx.fbn.nevernote.NeverNote.remoteConnect(NeverNote.java:3422)
	at cx.fbn.nevernote.NeverNote.<init>(NeverNote.java:721)
	at cx.fbn.nevernote.NeverNote.main(NeverNote.java:807)
Caused by: javax.net.ssl.SSLException: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at sun.security.ssl.Alerts.getSSLException(Alerts.java:208)
	at sun.security.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1697)
	at sun.security.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1660)
	at sun.security.ssl.SSLSocketImpl.handleException(SSLSocketImpl.java:1643)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1224)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1201)
	at sun.net.www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:440)
	at sun.net.www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:185)
	at sun.net.www.protocol.https.HttpsURLConnectionImpl.connect(HttpsURLConnectionImpl.java:153)
	at org.apache.thrift.transport.THttpClient.flush(THttpClient.java:142)
	... 6 more
Caused by: java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at sun.security.validator.PKIXValidator.<init>(PKIXValidator.java:75)
	at sun.security.validator.Validator.getInstance(Validator.java:178)
	at sun.security.ssl.X509TrustManagerImpl.getValidator(X509TrustManagerImpl.java:129)
	at sun.security.ssl.X509TrustManagerImpl.checkServerTrusted(X509TrustManagerImpl.java:225)
	at sun.security.ssl.X509TrustManagerImpl.checkServerTrusted(X509TrustManagerImpl.java:270)
	at sun.security.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1144)
	at sun.security.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:154)
	at sun.security.ssl.Handshaker.processLoop(Handshaker.java:609)
	at sun.security.ssl.Handshaker.process_record(Handshaker.java:545)
	at sun.security.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:945)
	at sun.security.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1190)
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1217)
	... 11 more
Caused by: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
	at java.security.cert.PKIXParameters.setTrustAnchors(PKIXParameters.java:200)
	at java.security.cert.PKIXParameters.<init>(PKIXParameters.java:120)
	at java.security.cert.PKIXBuilderParameters.<init>(PKIXBuilderParameters.java:104)
	at sun.security.validator.PKIXValidator.<init>(PKIXValidator.java:73)
	... 22 more
Goodbye.

```

---

### Post by effenberg0x0 on 2012-02-21
I am running Nixnote (and able to sync it to Evernote) right now. The only particularity of my setup that can be related to this is that I use jre1.6.0_30. A default install of PP would not have it installed by default. 

Also, try renaming your .nevernote folder to something like .nevernote.backup and restart the application. I've seen nixnote corrupt this folder a couple times.

Regards,
Effenberg

---

### Post by donniezazen on 2012-02-21
> **effenberg0x0 said:**
> I am running Nixnote (and able to sync it to Evernote) right now. The only particularity of my setup that can be related to this is that I use jre1.6.0_30. A default install of PP would not have it installed by default. 

Also, try renaming your .nevernote folder to something like .nevernote.backup and restart the application. I've seen nixnote corrupt this folder a couple times.

Regards,
Effenberg

Where and what package did you install to get jre? I have installed openjdk-7-jre and iceadtea-7-plugin which seems to have installed a lot off packages. Their should be nothing in .nevernote because it is a clean install and never been synced.

---

### Post by effenberg0x0 on 2012-02-21
> **donniezazen said:**
> Where and what package did you install to get jre? I have installed openjdk-7-jre and iceadtea-7-plugin which seems to have installed a lot off packages. Their should be nothing in .nevernote because it is a clean install and never been synced.

Hey,

Not a package, as we don't have it anymore on the repos. I have all JREs installed directly through Oracle binary files from [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html) . A number of applications I (unfortunately) use won't work with OpenJDK and IcedTea... 

In my case, I defined this jvms as alternatives. Then I use sudo update-alternatives --config java to adjust the softlinks to java, javac, javaws, etc so they point to the desired /lib/jvm/<version>/java_stuff. I also have created scripts that use specific versions directly when launching some programs. Anyway, just get the path for java in the directory where you downloaded/extracted Java6 and fix /usr/share/nixnote/nixnote.sh to use it.

Regards,
Effenberg

---

### Post by donniezazen on 2012-02-22
> **effenberg0x0 said:**
> Hey,

Not a package, as we don't have it anymore on the repos. I have all JREs installed directly through Oracle binary files from [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html) . A number of applications I (unfortunately) use won't work with OpenJDK and IcedTea... 

In my case, I defined this jvms as alternatives. Then I use sudo update-alternatives --config java to adjust the softlinks to java, javac, javaws, etc so they point to the desired /lib/jvm/<version>/java_stuff. I also have created scripts that use specific versions directly when launching some programs. Anyway, just get the path for java in the directory where you downloaded/extracted Java6 and fix /usr/share/nixnote/nixnote.sh to use it.

Regards,
Effenberg

Thanks, that sounds complicated. I came back on Oneiric for a while and installed Sun Java from [https://launchpad.net/~ferramroberto/+archive/java](https://launchpad.net/~ferramroberto/+archive/java). Not all of my notebooks are being synced. I am looking into it.

Thank you.

---

