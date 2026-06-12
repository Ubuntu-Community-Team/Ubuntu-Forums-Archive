---
title: "How to assigned a T1 port to an specific extension"
date: 2009-10-02
forum: Server Platforms
---

### Post by jhon78 on 2009-10-02
Some information...

I have configured the PBX G3r from AVAYA to the Asterisk box through a T1 link, in the PBX side I dont have a trunk group, I use each one of the channel ports from the T1 as an station, this means that 1 port is know in the PBX as an extension, example: extension 3000 is the channel 1 from the 23 channels in the T1, 3001 is the channel 2 from the 23 channels in the T1....

So when someone call from one extension in the PBX example 4000 to the extension 3000 the call goes to the asterisk box, so the question here is: how can I assigned each one of the port from the T1 to an especific sip extension in the asterisk box, example from the full path call from an extension in the PBX to an specific extension in the asterisk box:

AVAYA extension that is calling ---> AVAYA DS1FD extension(T1 port) ---> Specific Sip extension
Example
4000 (From AVAYA PBX) ----> 3000(Virtual Extension Port 1 T1 link) ---> 2000 (Sip extension in the Asterisk)

I have all configurated, the only part I am looking is how to assigned the specific port to a specific sip extension in the Asterisk box.

Other option is to create a pool extension in the asterisk to send the call to a bounch of extension.
If you have any idea just let me know it.

Best regards:popcorn:

---

