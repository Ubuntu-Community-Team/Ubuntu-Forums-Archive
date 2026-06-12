---
title: "Java sound problem on Gazelle"
date: 2008-07-12
forum: System76 Support
---

### Post by sandygmaharaj on 2008-07-12
When I try to run SIP communicator ([www.sip-communicator.org](www.sip-communicator.org)), I get the following error:
```

 sip-communicator -v

Welcome to Felix.
=================

Cannot open audio device for input: javax.sound.sampled.LineUnavailableException: line with format PCM_SIGNED 44100.0 Hz, 16 bit, stereo, 4 bytes/frame, little-endian not supported.
Failed to configure: com.sun.media.ProcessEngine@1117a20
  IO exception: line with format PCM_SIGNED 44100.0 Hz, 16 bit, stereo, 4 bytes/frame, little-endian not supported.

Error: Unable to configure com.sun.media.ProcessEngine@1117a20
20:06:27.141 SEVERE: impl.media.MediaServiceImpl.run().401 Failed to initialize media control
net.java.sip.communicator.service.media.MediaException: Media manager could not configure processor
for the specified data source
	at net.java.sip.communicator.impl.media.MediaControl.initProcessor(MediaControl.java:528)
	at net.java.sip.communicator.impl.media.MediaControl.initCaptureDevices(MediaControl.java:421)
	at net.java.sip.communicator.impl.media.MediaControl.initialize(MediaControl.java:213)
	at net.java.sip.communicator.impl.media.MediaServiceImpl$DeviceConfigurationThread.run(MediaServiceImpl.java:395)
	at net.java.sip.communicator.impl.media.MediaServiceImpl.start(MediaServiceImpl.java:224)
	at net.java.sip.communicator.impl.media.MediaActivator.start(MediaActivator.java:60)
	at org.apache.felix.framework.util.SecureAction.startActivator(SecureAction.java:589)
	at org.apache.felix.framework.Felix._startBundle(Felix.java:1536)
	at org.apache.felix.framework.Felix.startBundle(Felix.java:1470)
	at org.apache.felix.framework.Felix.setFrameworkStartLevel(Felix.java:1065)
	at org.apache.felix.framework.StartLevelImpl.run(StartLevelImpl.java:258)
	at java.lang.Thread.run(Thread.java:619)
20:06:28.891 SEVERE: impl.gui.UIServiceImpl.serviceChanged().645 Plugin Component type is not supported.Should provide a plugin in AWT, SWT or Swing.
```


Interesting line here is;
[B]javax.sound.sampled.LineUnavailableException: line with format PCM_SIGNED 44100.0 Hz, 16 bit, stereo, 4 bytes/frame, little-endian not supported.
[/B]
This program works fine on a Compaq system with ubuntu. What could be wrong?

---

### Post by thomasaaron on 2008-07-14
```
645 Plugin Component type is not supported.Should provide a plugin in AWT, SWT or Swing
```

That's the important line. Either there is something about your sound card not supported by Java, or your JVM is having difficulty dealing with the program.

My gut feeling is that you are using java-6-openjdk to provide java on your system. Open JDK isn't quite ready for the big leagues yet. Try this...


```
sudo apt-get install sun-java6-jdk  #Install Sun's Java
```  
```
sudo update-alternatives --config java  #Select the number that corresponds to Sun's Java.
```  
```
sudo reboot
```

Now retry your program.

---

