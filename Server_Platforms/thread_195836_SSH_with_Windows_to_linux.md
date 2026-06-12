---
title: "SSH with Windows to linux"
date: 2006-06-13
forum: Server Platforms
---

### Post by Isoss on 2006-06-13
I have an ubuntu server with openssh-server. from my laptop, which has ubuntu dapper desktop, I can ssh to the the PC which has ubuntu server. How can I ssh from other windows machines on the network?

---

### Post by rbalfour on 2006-06-13
for windows get putty

it's a FREE client for windows.
[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

---

### Post by Isoss on 2006-06-13
Thanks. I'll download it and try.

---

### Post by Isoss on 2006-06-13
Hey, Thanks a lot. It's not what I am asking though! But thanks cuz I was about to post about this program cuz I have heard of but didn't remember it's name. 
My question was How to SSH With folders, that is, accessing folders like /var/www with a full permission.

So this is exatly what I need and thanks for the prog cuz that's something I've been looking for anyway.

I also need to know how to access the localhost on my ubuntu server from IE on windows machines on the network. I tried [http://192.168.0.1](http://192.168.0.1) which is the PCs IP on the network but didn't work neither with IE in windows nor with firefox in my linux on my laptop. if you konw thye solution please post [here]("http://ubuntuforums.org/showthread.php?t=195829"). It's a post of my problem with accessing localhost of the ubuntuserver from my laptop. Everything works fine on the ubuntu server, apache is running, port 80 is opened. Concerning this problem I wish you'd post there. But if you have a solution for SShing with folders please post here.

Thanks

---

### Post by ScatterBrain on 2006-06-13
What you need then is WinSCP - google for it.  It and putty are on all of my windows boxen.

---

### Post by harisund on 2006-06-13
If you want to log in and execute commands, you will have to use putty. 
If you want to transfer files around, you will have to use Filezilla. 

If you want to do both simultaneously using one program however, you will have to install Cygwin. 

Cygwin is a very powerful and amazing program, but I would suggest you use Putty to login and execute commands and use Filezilla to move files around.

---

### Post by haircut on 2006-06-14
Scatterbrain is right, use WinSCP: [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

You use the same SSH port as well, saying that I do believe that FileZilla can do the same thing as it has some parts of the pUTTY code built into it.

---

### Post by Isoss on 2006-06-14
Alright thanks guys, I'll google around and try to get them and then I'll report to u what happens.

---

### Post by Isoss on 2006-06-17
Hey ScatterBrain, thanks a lot this is exactly what I've been looking for. I also would like to get something like that for linux. I mean when I first downloaded PuTTY I liked it so much and when I found a linux PuTTY in synaptic I got even happier! ... I liked that feeling so I hope I'd feel it again when I find something just like WinSCP for linux machines ;)

Thanks a lot for your help guys:)

---

### Post by hesoez on 2006-06-18
I use nautilus(locations->connect to server) or sometimes gftp for file-transfer over ssh

---

### Post by Isoss on 2006-06-18
WOW, Good idea ... it's working with gftp, thanks!

---

### Post by Isoss on 2006-06-18
Sorry I thought I did it with gftp but it actually didn't work ... if I would use FTP what port should I use?

What about the file-transfere over SSH? do u mean Places->Connect To Server then you choose server, port, username, folder and connection name? I tried that and it was working before and then it stopped working and began pormpting me with an error, check it [HERE]("http://ubuntuforums.org/showthread.php?t=198771")

Hope somebody has a solution.
Thanks.

---

### Post by hesoez on 2006-06-22
in gft:
where you fill in host,port,username and password there is a dropdown box at the end, select SSH2(now the port will be 22 unless u fill in another).
in nautilus:
the first selection is a dropdown box, select SSH there.

it works for me, i use ssh to transfer files back and forth with my server.
if you use nautilus it will show up in a regular window so you can drag and drop like you can with a local directory.

grtz

---

### Post by Isoss on 2006-06-23
Cool .. Now it works .. Thanks a bunch!

---

