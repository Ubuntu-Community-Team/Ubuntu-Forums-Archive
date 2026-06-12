---
title: "Microphone Recording distorts..of a ."
date: 2010-07-31
forum: System76 Support
---

### Post by jpelorat on 2010-07-31
Hi,

I'm the happy owner of a panp5. Recently decided to use Skype to communicate with some friends. Configuring the microphone options through the Skype test procedure I realize that everything that is recorded gets distorted as it was done by a sick Darth Vader.

My system details are:

Laptop-> System 76 Pangolin Performance (panp5)
OS-> kubuntu 10.04 64 bits
Audio Hardware-> ALC662
AudioModule-> Intel HDA

Any idea on how to deal with this or what can be possible going wrong?

Thanks in advance,
Ziggy...

---

### Post by isantop on 2010-08-03
Can you try recording with a different application? Let's see if skype is the problem or your configuration.

---

### Post by jpelorat on 2010-08-03
Thanks for your reply.

I didn't think of trying other applications. Lazy me! I tried with Audacity and the voice recording went well. It means is a Skype Issue.

Ziggy...

---

### Post by isantop on 2010-08-03
I'll see if I can get skype going on a computer here and post a screenshot of my configuration.

---

### Post by jpelorat on 2010-08-15
Thanks. I've been trying to look for a solution through Skype, but nothing so far. 

> **isantop said:**
> I'll see if I can get skype going on a computer here and post a screenshot of my configuration.

---

### Post by jpelorat on 2010-08-19
Any idea about this: https://jira.skype.com/browse/SCL-454?page=com.atlassian.jira.plugin.system.issuetabpanels%3Aall-tabpanel

---

### Post by isantop on 2010-08-19
Sounds like that is the problem. Can you find out exactly which version of skype you're using?

---

### Post by mattcasters on 2010-09-08
I installed PulseAudio and the "Jabba the hut" sound distortion issue in Skype went away.

---

### Post by jpelorat on 2010-09-08
> **isantop said:**
> Sounds like that is the problem. Can you find out exactly which version of skype you're using?

I&#7743; using the Skype version 2.1.0.81 :-)

---

### Post by jpelorat on 2010-09-08
> **isantop said:**
> Sounds like that is the problem. Can you find out exactly which version of skype you're using?

Thanks... This works but the audio through Phonon stops working when Skype is active. I could work it out using Skype alone when needed and Amarok and the other stuff when Skype off.  Now I'll try to find a way to make PulseAudio and Phonon work together without disturbing each other. any ideas?

---

### Post by isantop on 2010-09-08
I don't have any right off the bat. Are you using the 1.4 version now?

---

### Post by jpelorat on 2010-09-08
> **isantop said:**
> I don't have any right off the bat. Are you using the 1.4 version now?

Hi... i'm using the Skype version 2.1.0.81...

---

### Post by jpelorat on 2010-11-08
> **jpelorat said:**
> Thanks... This works but the audio through Phonon stops working when Skype is active. I could work it out using Skype alone when needed and Amarok and the other stuff when Skype off.  Now I'll try to find a way to make PulseAudio and Phonon work together without disturbing each other. any ideas?

Sorry to let this thread open for so long. I got to a KDE page where they announce they have serious problems with PulseAudio and that they will have this issue followed on their future development. I also migrate to Kubuntu 10.10 and the inconsistencies between Phonon and PulseAudio continue. I decided to just turn on PulseAudio to use Skype and, after using it return to Phonon, hopping KDE audio applications won't hangup.

So, this will be all on my behalf about this issue. 

Thanks all for your help and patience.

Zigggy :-)

---

