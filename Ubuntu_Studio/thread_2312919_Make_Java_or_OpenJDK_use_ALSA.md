---
title: "Make Java or OpenJDK use ALSA"
date: 2016-02-08
forum: Ubuntu Studio
---

### Post by marseille2 on 2016-02-08
I wanted to test the Java drummachine "[orDrumbox]("http://www.ordrumbox.com/index.php")" (using OpenJDK 7), but discovered it wouldn't open without pulseaudio (PA). In fact, since I shut PA off, and use ALSA loopback ... listening to audio through any Java program wasn't an option, since PA is the default sound setting. So I had to dig around to figure it out, and thought I'd share to save someone else time.

To use ALSA with Java or OpenJDK, edit the '**sound.properties**' file. If you're using OpenJDK7, find it in **/etc/java-7-openjdk** (Oracle's Java directory should be in /etc, too). 

To simply read the file:

```
$ more /etc/java-7-openjdk/sound.properties
```

Editing the file is not so bad. It's just a matter of and commenting out pulseaudio, and removing the hash tag from a few more.
 
```
$ sudo gedit  /etc/java-7-openjdk/sound.properties
```

Change:

```
javax.sound.sampled.Clip=org.classpath.icedtea.pulseaudio.PulseAudioMixerProvider
javax.sound.sampled.Port=org.classpath.icedtea.pulseaudio.PulseAudioMixerProvider
javax.sound.sampled.SourceDataLine=org.classpath.icedtea.pulseaudio.PulseAudioMixerProvider
javax.sound.sampled.TargetDataLine=org.classpath.icedtea.pulseaudio.PulseAudioMixerProvider


#javax.sound.sampled.Clip=com.sun.media.sound.DirectAudioDeviceProvider
#javax.sound.sampled.Port=com.sun.media.sound.PortMixerProvider
#javax.sound.sampled.SourceDataLine=com.sun.media.sound.DirectAudioDeviceProvider
#javax.sound.sampled.TargetDataLine=com.sun.media.sound.DirectAudioDeviceProvider
```


TO:

```

#javax.sound.sampled.Clip=org.classpath.icedtea.pulseaudio.PulseAudioMixerProvider
#javax.sound.sampled.Port=org.classpath.icedtea.pulseaudio.PulseAudioMixerProvider
#javax.sound.sampled.SourceDataLine=org.classpath.icedtea.pulseaudio.PulseAudioMixerProvider
#javax.sound.sampled.TargetDataLine=org.classpath.icedtea.pulseaudio.PulseAudioMixerProvider


javax.sound.sampled.Clip=com.sun.media.sound.DirectAudioDeviceProvider
javax.sound.sampled.Port=com.sun.media.sound.PortMixerProvider
javax.sound.sampled.SourceDataLine=com.sun.media.sound.DirectAudioDeviceProvider
javax.sound.sampled.TargetDataLine=com.sun.media.sound.DirectAudioDeviceProvider
```

---

