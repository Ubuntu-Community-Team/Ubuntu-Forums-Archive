---
title: "Starting up Ventrilo Server?"
date: 2010-06-23
forum: Server Platforms
---

### Post by Nolam on 2010-06-23
I have it downloaded (linux version). What folder should I put it in?? Does it matter?

I am new to bash so i dont know how to start the Ventrilo Server up.

I navigated to the folder the server is in and did ./ventrilo_srv and ./ventrilo_srv -d and they both come up "No such file or directory". What do i do???????

---

### Post by WinstonChurchill on 2010-06-23
> **Nolam said:**
> I have it downloaded (linux version). What folder should I put it in?? Does it matter?

I am new to bash so i dont know how to start the Ventrilo Server up.

I navigated to the folder the server is in and did ./ventrilo_srv and ./ventrilo_srv -d and they both come up "No such file or directory". What do i do???????
You know, I had this exact same issue with Ventrilo about 4 months ago - the file existed, I could use the 'vi' command and see it's contents, 'hexdump' would show it, and the permissions were set correctly (I tried a thousand configurations, even SUID), but whenever I tried to execute the file it would always give me that "file not found" error, even if I renamed it and moved it around. I tried extracting the archive on different machines with different programs and just moving the binary onto the server. I tried running it as several different users, including root. I tried executing the binary from scripts - absolutely nothing worked. It makes no sense at all... the file was right there, but BASH always threw up that error message.... I really thought I was going crazy. Ventrilo worked fine on my old server (not certain that it was the same version though); the only difference I can think of is that my new server is x86_64 and my old one was 32-bit; is yours? Run 'uname -m' and see what the output is. Maybe there is some strange incompatibility? I really have no idea.

I gave up because I didn't ever use it much anyway - but if you really need Ventrilo-like functionality, Mumble is open-source and supposedly works better anyway. It has clients ported to all the major operating systems. I'd just go with that. Just run:```
sudo apt-get install mumble-server
```... and then read the man pages and set up your config files as you like.

---

### Post by Nolam on 2010-06-23
You know what...mine is too...and the ventrilo server is only 32-bit...could that be it for some weird reason??? Because other people got it to work but i dont know if they have 32 or 64 bit.

I reinstalled my server (there was nothing on it) as 32 bit, and it worked!!! Thank you so much!!!

Now, the screen comes up and its running, but is there a way to somehow minimize this and put it in the background and go do something else or something??

---

### Post by Eric Buist on 2012-12-23
> **Nolam said:**
> You know what...mine is too...and the ventrilo server is only 32-bit...could that be it for some weird reason??? Because other people got it to work but i dont know if they have 32 or 64 bit.

I reinstalled my server (there was nothing on it) as 32 bit, and it worked!!! Thank you so much!!!

Now, the screen comes up and its running, but is there a way to somehow minimize this and put it in the background and go do something else or something??

Very strange indeed, and very shocking... until you run sudo apt-get install ia32-libs. This solved it, at least for me, on Ubuntu 12.10. Now the server is running, but I will experiment with Mumble since there is no Ventrilo client for Linux anyway.

---

### Post by overdrank on 2012-12-23
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

