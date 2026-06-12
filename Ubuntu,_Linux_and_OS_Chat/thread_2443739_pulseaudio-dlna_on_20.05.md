---
title: "pulseaudio-dlna on 20.05"
date: 2020-05-19
forum: Ubuntu, Linux and OS Chat
---

### Post by bill-wilken-wilkenmail on 2020-05-19
Before 18.04, I was able to stream music to my Marantz DLNA server.  Yesterday, I decided it was time to set up my 20.04 desktop to do the same, but when I searched Synaptic for the necessary PulseAudio-dlna module, it was nowhere to be found.  The latest binary published specifically for Ubuntu dates back to 17.04.  Not to be discouraged, I downloaded and installed the most recent pure Debian variant.  While it indicates that it is transmitting sound to the Marantz unit, the unit sits silent.  I'm wondering whether anyone has any success in downloading and compiling the source.  For the time being, I'm streaming my 20.04 library via a Kodi server sitting on networked Mac.

---

### Post by bill-wilken-wilkenmail on 2020-05-23
Upon further digging, I discovered that pulseaudio-dlna was updated for Ubuntu 19.10.  It works nicely with 20.04, but requires a few python dependencies that also are not included with 20.04.  After installing everything, however, I spent a few frustrating moments getting the module to work, having forgotten that it is not executed by the pulseaudio module. It must be executed separately.  If you plan to use it regularly, I suggest loading it automatically as a start-up application.

---

