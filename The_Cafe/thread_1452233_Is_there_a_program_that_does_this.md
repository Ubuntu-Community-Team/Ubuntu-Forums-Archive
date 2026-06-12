---
title: "Is there a program that does this?"
date: 2010-04-11
forum: The Cafe
---

### Post by dragos240 on 2010-04-11
Hi,

I am trying to make the chu chu rocket network again. They shut down the online servers in 2003. What I'm trying to do is connect a phone line from the dreamcast to my computer, and see what address the game is trying to ask for. For example:

Game asks for ip address:
45.456.34.123

I want to track what requests the game makes.

Is there a program that can do this?

---

### Post by dragos240 on 2010-04-11
Anyone?

---

### Post by new_tolinux on 2010-04-11
I don't know how you get that done by using a phone-line.

Although if you can do it by LAN-proxy, almost every software is capable of logging what addresses are requested.

---

### Post by juancarlospaco on 2010-04-11
***Whats a chu chu network?***

:s

---

### Post by dragos240 on 2010-04-11
> **new_tolinux said:**
> I don't know how you get that done by using a phone-line.

Although if you can do it by LAN-proxy, almost every software is capable of logging what addresses are requested.

The DC did online gaming via dial-up (How, I don't know).

So I will need to use a phone line for this.

---

### Post by chappajar on 2010-04-11
> **dragos240 said:**
> Hi,

I am trying to make the chu chu rocket network again. They shut down the online servers in 2003. What I'm trying to do is connect a phone line from the dreamcast to my computer, and see what address the game is trying to ask for. For example:

Game asks for ip address:
45.456.34.123

I want to track what requests the game makes.

Is there a program that can do this?

Wireshark.

---

### Post by Frak on 2010-04-12
Proxy redirect to the appropriate servers. Every OS has its own way of doing it.

---

### Post by RetroGO on 2010-04-13
> **chappajar said:**
> Wireshark.
I agree. Wireshark would do the job of telling you what traffic is coming from the Dreamcast.

I'm very interested in your project, dragos. I actually found this forum by searching for Chu Chu Rocket Online (after seeing your post on the DCForums).

I'd love to help out if I can, but I think you (we) might be fighting a losing battle.

Chu Chu Rocket ran on Sega SNAP (Sega Network Application Package) which was later sold to Nokia for use with the N-Gage. I think it's going to be near impossible to emulate SNAP servers without either getting hold of a copy of SNAP, or the Chu Chu Rocket source code. I'd love to be proven wrong though!

I guess this is a bit beyond what the Ubuntu forum is meant for though, so you might be best PMing me your email address so we can share ideas/information.

---

### Post by dragos240 on 2010-04-13
> **RetroGO said:**
> I agree. Wireshark would do the job of telling you what traffic is coming from the Dreamcast.

I'm very interested in your project, dragos. I actually found this forum by searching for Chu Chu Rocket Online (after seeing your post on the DCForums).

I'd love to help out if I can, but I think you (we) might be fighting a losing battle.

Chu Chu Rocket ran on Sega SNAP (Sega Network Application Package) which was later sold to Nokia for use with the N-Gage. I think it's going to be near impossible to emulate SNAP servers without either getting hold of a copy of SNAP, or the Chu Chu Rocket source code. I'd love to be proven wrong though!

I guess this is a bit beyond what the Ubuntu forum is meant for though, so you might be best PMing me your email address so we can share ideas/information.

Heh, I don't think it would be that hard. The chu chu rocket network needed servers to chat, and find a place were other players could lobby. However, gameplay was point to point, so to speak. If you watch the "last chu chu rocket battle" video (or something like that). The game was still playing after the servers were shut down. So at least the gameplay could be emulated. It doesn't look too hard.

---

### Post by RetroGO on 2010-04-13
> **dragos240 said:**
> Heh, I don't think it would be that hard. The chu chu rocket network needed servers to chat, and find a place were other players could lobby. However, gameplay was point to point, so to speak. If you watch the "last chu chu rocket battle" video (or something like that). The game was still playing after the servers were shut down. So at least the gameplay could be emulated. It doesn't look too hard.
Well, should I say it'd be hard for me to do, because I wouldn't know where to start! :P

So how far have you got? Or are you only just starting out?

---

### Post by dragos240 on 2010-04-13
> **RetroGO said:**
> Well, should I say it'd be hard for me to do, because I wouldn't know where to start! :P

So how far have you got? Or are you only just starting out?

Technically speaking, I'm just starting. But I would start with seeing if an empty server with nothing running will host it. If not, I'll need some help. But it shouldn't be THAT complex. After all, we're trying to emulate a 10 year old server application.

---

### Post by RetroGO on 2010-04-13
> **dragos240 said:**
> Technically speaking, I'm just starting. But I would start with seeing if an empty server with nothing running will host it. If not, I'll need some help. But it shouldn't be THAT complex. After all, we're trying to emulate a 10 year old server application.
I can tell you now, that's not going to work. I work in networking, and an 'empty server with nothing running' NEVER does anything when you connect to it. You always need something there :P

And yes, the server software is 10 years old, but so is Windows XP. Can you emulate that?

Maybe the server software is simple and easy to emulate/replicate, but I don't know how you're planning about doing that out of thin air without having anything to go by first?

Have you got any experience doing stuff like this before? I'm guessing not?

---

### Post by dragos240 on 2010-04-13
> **RetroGO said:**
> I can tell you now, that's not going to work. I work in networking, and an 'empty server with nothing running' NEVER does anything when you connect to it. You always need something there :P

And yes, the server software is 10 years old, but so is Windows XP. Can you emulate that?

Maybe the server software is simple and easy to emulate/replicate, but I don't know how you're planning about doing that out of thin air without having anything to go by first?

Have you got any experience doing stuff like this before? I'm guessing not?

Well I can run 10 year old software with wine, but I can't emulate it, because wine is NOT an emulator, rather an application compatibility layer. Anyway, I meant opening a blank port, and the server will listen for a connection. I'm sure this is possible, I have no clue how long it will take to do it. Wine took 10 years (but in that time it works amazingly.)

---

### Post by RetroGO on 2010-04-14
Have you managed to find the IP address, or DNS name that Chu Chu is looking for yet? I'd try myself, but my DC's modem doesn't like to connect to computers. I'll have to try and get another one that's compatible.

---

### Post by BackwardsDown on 2010-04-14
> Anyway, I meant opening a blank port, and the server will listen for a connection. I'm sure this is possible, I have no clue how long it will take to do it.

Yes, with python you could open a port and start listening. But what what do you expect? Python gets the message 'hey I want to connect' from the dreamcast. And then what? Probably nothing. Your server is not going to anything, and you dreamcast will be waiting for a response.

---

