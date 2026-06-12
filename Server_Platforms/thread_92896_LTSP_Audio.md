---
title: "LTSP Audio"
date: 2005-11-20
forum: Server Platforms
---

### Post by Ububurns on 2005-11-20
LTSP is workingfine.  I can connect client PCs to the server - and it's absoultely fantastic.

However when a client wants to play a video or music, the audio is coming out of the SERVER'S speakers.  It's kind of cool (but not what I want :D )

Is there any way I can get the client PCs to play audio locally instead?

---

### Post by garyng on 2005-11-21
[QUOTE=Ububurns]LTSP is workingfine.  I can connect client PCs to the server - and it's absoultely fantastic.

However when a client wants to play a video or music, the audio is coming out of the SERVER'S speakers.  It's kind of cool (but not what I want :D )

Is there any way I can get the client PCs to play audio locally instead?[/QUOTE]

esound demon. Basically, on the server the sound stream is pipe to a socket on your client workstation(where the demon is run) where it is output to the local speaker.

Most popular player supports it.

The only thing I don't like it(comparing with Windows RDP) is that you need to do some login shell script magic to create the necessary environment variable telling these programs where the socket is.

---

### Post by heisters on 2005-11-21
It also shouldn't be hard to do this with Jack. That would also offer you more flexibility than esound. Note also that you can create an alsa plugin for jack with a simple edit to Jack's config file so that any alsa (or even alsa-oss emulated) program can input to Jack.

---

### Post by garyng on 2005-11-21
[QUOTE=heisters]It also shouldn't be hard to do this with Jack. That would also offer you more flexibility than esound. Note also that you can create an alsa plugin for jack with a simple edit to Jack's config file so that any alsa (or even alsa-oss emulated) program can input to Jack.[/QUOTE]
How does jack work ? I don't quite get it on their site, especially in this context.

---

### Post by Ububurns on 2005-11-24
Thanks for your suggestions guys!

However I think it's more the fact (please correct me if I'm wrong!) that LTSP clients don't actually detect local hardware and set it up to use - the clients just keep the server's configuration.  Thus, my client thinks it has my server's sound card, video card, hard drives - It doesn't care what it physically has.  (Which in this case, I don't want!)

I'm probably over-simplifying everything, and asking for the impossible - but perhaps my question could be rephrased as such:  Can the LTSP setup be modified so that when the client PC boots, it detects some of its own hardware to use?  Or, can I give an LTSP client the abilty to mount local media?

I understand the topic is now much broader now - any help would be great!

---

### Post by Yagisan on 2005-11-24
[QUOTE=Ububurns]Thanks for your suggestions guys!

However I think it's more the fact (please correct me if I'm wrong!) that LTSP clients don't actually detect local hardware and set it up to use - the clients just keep the server's configuration.  Thus, my client thinks it has my server's sound card, video card, hard drives - It doesn't care what it physically has.  (Which in this case, I don't want!)[/quote]
Correct - I was also amused to be at my server when the clients where logging in - I had a lot of ubuntu login chimes

[QUOTE=Ububurns]I'm probably over-simplifying everything, and asking for the impossible - but perhaps my question could be rephrased as such:  Can the LTSP setup be modified so that when the client PC boots, it detects some of its own hardware to use?  Or, can I give an LTSP client the abilty to mount local media?

I understand the topic is now much broader now - any help would be great![/QUOTE]Currently no, but it is being worked on for dapper. you can get general breezy ltsp help at #edubuntu

---

### Post by garyng on 2005-11-24
[QUOTE=Ububurns]Thanks for your suggestions guys!

However I think it's more the fact (please correct me if I'm wrong!) that LTSP clients don't actually detect local hardware and set it up to use - the clients just keep the server's configuration.  Thus, my client thinks it has my server's sound card, video card, hard drives - It doesn't care what it physically has.  (Which in this case, I don't want!)

I'm probably over-simplifying everything, and asking for the impossible - but perhaps my question could be rephrased as such:  Can the LTSP setup be modified so that when the client PC boots, it detects some of its own hardware to use?  Or, can I give an LTSP client the abilty to mount local media?

I understand the topic is now much broader now - any help would be great![/QUOTE]

Yes. Mounting local drive is also possible, as well as video card. But I don't think works out of the box and need some tweaks.

---

### Post by razametal on 2006-02-06
Does any one configured the terminals to mount local media as cdrom and floppy ?

Can you show us the lts.conf portion for this configuration ?

---

