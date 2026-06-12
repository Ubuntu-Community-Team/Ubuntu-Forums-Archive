---
title: "openjdk a little broken upon install"
date: 2016-03-08
forum: Ubuntu Development Version
---

### Post by ELD on 2016-03-08
It seems Ubuntu 16.04 openjdk is having issues with a number of games like Minecraft and Retro-Pixel Castles.

Here's a log of me trying to run Retro-Pixel Castles: [http://pastebin.com/7iGsV09t](http://pastebin.com/7iGsV09t)

The issue seems to be this:
> Caused by: java.lang.UnsatisfiedLinkError: /usr/lib/jvm/java-8-openjdk-amd64/jre/lib/ext/libatk-wrapper.so: /usr/lib/x86_64-linux-gnu/libatspi.so.0: undefined symbol: g_type_class_adjust_private_offset
I have libatk-wrapper installed, but it doesn't find it.

I asked about it on twitter and was told this:
> [COLOR=#292F33][FONT=HelveticaNeue]That has (almost) nothing to do with the game, the ATK Wrapper is broken in your distro, unfortunately.[/FONT][/COLOR]

> [COLOR=#292F33][FONT=HelveticaNeue]This codepath shouldn't fire at all if you don't have AT_SPI_IOR and AT_SPI_BUS props as reported by xprop. Is it so?[/FONT][/COLOR]

Could anyone shed light on this? Will be a problem for gamers at release if it's not fixed.

---

### Post by ELD on 2016-03-09
More info: All java games and apps work fine with Oracle Java, so it seems OpenJDK is just broken on Ubuntu 16.04 with the ATK wrapper.

---

### Post by kostkon on 2016-03-09
> **ELD said:**
> More info: All java games and apps work fine with Oracle Java, so it seems OpenJDK is just broken on Ubuntu 16.04 with the ATK wrapper.
OpenJDK8 to be precise. [Heartlands]("http://store.steampowered.com/app/336300") is affected as well.

The solution is to use OpenJDK7 which is also available in the repos.

After you install it, you can set the default jvm on your system by doing
```
sudo update-java-alternatives -l
```
to list the available jvms and then
```
sudo update-java-alternatives -s <jname>
```
to set it, e.g.
```
sudo update-java-alternatives -s java-1.7.0-openjdk-i386
```

---

### Post by ELD on 2016-03-11
Well, here's an example of Minecraft on OpenJDK 7 which does not work:

> Caused by: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty	at java.security.cert.PKIXParameters.setTrustAnchors(PKIXParameters.java:200) ~[?:1.7.0_95]
	at java.security.cert.PKIXParameters.<init>(PKIXParameters.java:120) ~[?:1.7.0_95]
	at java.security.cert.PKIXBuilderParameters.<init>(PKIXBuilderParameters.java:104) ~[?:1.7.0_95]
	at sun.security.validator.PKIXValidator.<init>(PKIXValidator.java:88) ~[?:1.7.0_95]
	at sun.security.validator.Validator.getInstance(Validator.java:179) ~[?:1.7.0_95]
	at sun.security.ssl.X509TrustManagerImpl.getValidator(X509TrustManagerImpl.java:314) ~[?:1.7.0_95]
	at sun.security.ssl.X509TrustManagerImpl.checkTrustedInit(X509TrustManagerImpl.java:173) ~[?:1.7.0_95]
	at sun.security.ssl.X509TrustManagerImpl.checkTrusted(X509TrustManagerImpl.java:186) ~[?:1.7.0_95]
	at sun.security.ssl.X509TrustManagerImpl.checkServerTrusted(X509TrustManagerImpl.java:126) ~[?:1.7.0_95]
	at sun.security.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1454) ~[?:1.7.0_95]
	at sun.security.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:213) ~[?:1.7.0_95]
	at sun.security.ssl.Handshaker.processLoop(Handshaker.java:913) ~[?:1.7.0_95]
	at sun.security.ssl.Handshaker.process_record(Handshaker.java:849) ~[?:1.7.0_95]
	at sun.security.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:1035) ~[?:1.7.0_95]
	at sun.security.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1344) ~[?:1.7.0_95]
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1371) ~[?:1.7.0_95]
	at sun.security.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1355) ~[?:1.7.0_95]
	at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:559)](www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:559)) ~[?:1.7.0_95]
	at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:185)](www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:185)) ~[?:1.7.0_95]
	at sun.net.[www.protocol.http.HttpURLConnection.getOutputStream(HttpURLConnection.java:1093)](www.protocol.http.HttpURLConnection.getOutputStream(HttpURLConnection.java:1093)) ~[?:1.7.0_95]
	at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getOutputStream(HttpsURLConnectionImpl.java:250)](www.protocol.https.HttpsURLConnectionImpl.getOutputStream(HttpsURLConnectionImpl.java:250)) ~[?:1.7.0_95]
	at com.mojang.authlib.HttpAuthenticationService.performPostRequest(HttpAuthenticationService.java:73) ~[launcher.jar:1.6.51]
	at com.mojang.authlib.yggdrasil.YggdrasilAuthenticationService.makeRequest(YggdrasilAuthenticationService.java:54) ~[launcher.jar:1.6.51]
	... 6 more




---

### Post by ELD on 2016-03-11
For some reason this fixes it:
> [COLOR=#111111][FONT=Consolas]sudo update-ca-certificates -f[/FONT][/COLOR]

---

