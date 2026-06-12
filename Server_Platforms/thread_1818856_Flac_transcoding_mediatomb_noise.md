---
title: "Flac transcoding mediatomb noise"
date: 2011-08-05
forum: Server Platforms
---

### Post by sev1985 on 2011-08-05
Hi 
First time poster 

I'm having a problem with mediatomb 
My player is a Samsung bd-5300 
My player will play the transcoded flac files, but there is noise like tape hiss and popping. 
If anyone can help it would be appreciated I've tried 3 buffer settings with the
same result 

Here's the transcoding profile 

      <profile name="flac2wav" enabled="yes" type="external">
        <mimetype>audio/L16</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <sample-frequency>44100</sample-frequency>
        <hide-original-resource>yes</hide-original-resource>
        <audio-channels>2</audio-channels>
        <agent command="flac" arguments="-d -f -o  %out %in"/>
        <buffer size="1048576" chunk-size="4096" fill-size="1024"/>
      </profile>

---

### Post by sev1985 on 2011-08-05
Bump

---

### Post by sev1985 on 2011-08-06
Bump

---

