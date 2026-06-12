---
title: "Question On 'Streamed Music'A question about this....if you listen to 'a stream' of m"
date: 2008-04-14
forum: Security Discussions
---

### Post by OrcaWave on 2008-04-14
A question about this....if you listen to 'a stream' of music, can someone else use (hack into) the music stream? And use it as 'a backdoor' into your computer.

I've heard several different answers to this question. Some were "Yes, it can happen", some were "No, it can't happen".

What do you guys believe about it? Can the stream of music be 'hacked' into, and used as 'a backdoor'?

What this would mean is that you have 'a Disk Jockey' using his (or her) computer to play this music, in say Oregon, it's broadcast 'live', and we listen to it in Nebraska.

Would there be a way to hack the DJ's computer in Oregon, and bring some bug into our computer that way.

Or, the music stream is "intercepted" and something harmful is inserted into the stream of music that we recieve on our end.

Could this be done, do you think?

---

### Post by HermanAB on 2008-04-14
Windows: Probably yes.
Linux: Probably not.

The biggest danger is that the DJ can start to play a Country or Hip-Hop song really loud and cause your ears to bleed...

Cheers,

herman

---

### Post by hyper_ch on 2008-04-14
I'd also say no likely on linux

---

### Post by Koori23 on 2008-04-14
Streaming music isn't actually downloaded to your machine. It's not like web browsing where tidbits are downloaded onto your harddrive. All you are doing is downloading a playlist file. 

If you were actively downloading and uploading the actual audo file, you'd run the risk but as far as I know, playlist files are a one way street.

---

### Post by Deathrend on 2008-04-14
it depends on how you're streaming.  If you're using something like Windows Media Server on Windows Server 2000/2003/2008, then you're fine. It's more the open sorce stuff you would want to be careful about.  I personally use Jinzora (Spelling?).  This is more of a two way streat however, giving me control over what I listen to, and/or watch (Streams movies too, quite well).

the downside to Jinzora, it takes responces as well, however it works like a webpage meaning you have to be inside the page to access that information.  

As for The Windows Mead, it's more like a Radio over the Air, meaning, you can listen, but you really have zero control over what it does.

---

### Post by HermanAB on 2008-04-14
There have been horrid exploits in Windows Media Player, so it is a real threat on a Windows machine, but on Linux things are much more secure.  The difference is that where on Linux you have multiple layers of security, on Windows you have multiple layers of insecurity...

---

### Post by netlogic on 2008-04-14
> **HermanAB said:**
> There have been horrid exploits in Windows Media Player, so it is a real threat on a Windows machine, but on Linux things are much more secure.  The difference is that where on Linux you have multiple layers of security, on Windows you have multiple layers of insecurity...

don't get me started about installing applications inside a media player by violating drm license schemes. there is no way to protect them, but most IT directors want their IT staff to turn water into wine.

---

### Post by The Tronyx on 2008-04-15
There is a lot of theory on how an active media exploit can take place but it gets fairly complicated.  You need to take into consideration whether it is the program or the process you are exploiting.  There are also flash players too though (and many other kinds as well).  Exploits (generally) are **not** a one-size-fits-all kind of thing meaning that just because you can exploit something in conjunction with one program does not mean that it can be exploited in conjunction with another program.

Suffice to say that exploitation of a media-based plugin on Linux would be insanely complicated.

---

### Post by netlogic on 2008-04-15
YEA MON!

However, in Windows creating a new thread by inserting dlls or cloning a similar running process to open up a new thread is doable. However, in Unix I believe new process has be started to link to a library or it has be to hijacked. I think that is why is so difficult to see Flash player hijacking in real Unix (everything but OSX).

---

