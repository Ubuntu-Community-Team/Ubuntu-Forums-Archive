---
title: "vsftp, users and file UL/DL"
date: 2006-01-25
forum: Server Platforms
---

### Post by CosMix on 2006-01-25
Hey,

Im pretty new to Linux, but very keen on learning (as is in my nature that im i curious :D). Ive had some contact with Linux before but never really knew how to work my way around things...especially in the console. Well, here i am, working my way through console (which is for me the best way to deal with things, coz' ur actually closer to the system itself and not hidding behind a end user GUI). However, ive installed ubuntu as a server without X Window server (the comp is old enough to be proclaimed extinct :)) and am browsing through the directories and getting to know commands and stuff. 

Since i want my comp to be running on the net 24/7 and i want it to earn its stay online, ive decided to build up a FTP server and maybe later even web and mail server...bingo! :D Ive bumped in this obstacle which is called lack of knowledge. Ive installed vsftpd and even made it run, but i somehow dont know what should i do now. I mean....do i only have to configure the vsftpd.conf file in order to make it work (coz ive kinda enabled some features) or do i have to work my way around somewhere else? I can even connect to the ftp server but i cant upload or create directories. And im stuck. As im writting this post, im also reading some net sources on vsftpd.conf. Hope ill get there by myself but i would aprettiate any help given the circumstance that im a complete begginer.

thnx a lot,

Gorazd,SI

p.s.: this is how my conf file looks like [-o< 


listen=YES
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
ascii_upload_enable=YES
ascii_download_enable=YES
ftpd_banner=Testni FTP streznik
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem

---

### Post by MJN on 2006-01-25
Hi CosMix,

What error message are you getting?

Do you still get the errors if you ftp from the same machine (i.e. **ftp 127.0.0.1**) and then try and create a directory?

Mathew

---

### Post by CosMix on 2006-01-25
Hey Mathew :D


if i log in as an anonymous user i cant create a directory...which is kinda good :D (desired) if i log as a local user...i can (weee :)). But this is only as log as i connect to 127.0.0.1 As soon as i try to connect form outside, i cant create nor upload. :confused: 

any pointers where to look, what to check ?

Gorazd

P.S. #1 : I think ive already figured it out while im going through the conf file step by step....i think that the conf file 
             i was using now, was just a sample and very incomplete (stripped of its features). Hope so...i hope im not 
             in a dead alley and about to hit the wall :p

---

### Post by MJN on 2006-01-25
Okay.

From 'outside' can you even list the directory? The rest assumes you can't....

Try adding the following to your /etc/vsftpd.conf file (and restarting - now you know how! ;)):

```

pasv_enable=YES
pasv_min_port=3000
pasv_max_port=3010
pasv_address=<your public IP address> (this address is the address that outside connections come in on)

``` 
If you have a router/firewall you'll need to forward TCP ports 3000-3010 to your FTP server.

Given this a go and if it works I'll let you know why, if not we can look a bit further...

Mathew

P.S. You could avoid the problem altogether, whilst also providing far more security, if you ditch FTP and install an SSH server instead - far simpler to configure and far more secure (everything's encrypted in transit)... the choice is yours... ;)

---

### Post by CosMix on 2006-01-25
Excuse me....but what has SSH to do with FTP ?

:-k 

Gorazd

---

### Post by Neg127 on 2006-01-26
SSH hs a feature where you can SCP files rather then using plane text protocall like FTP.  Any time you log in to a machine over the FTP protocall all user names and passwords are sent in clear text and can be sniffed.  When you SCP files or directories etc, all usernames passwords and files are encrypted.  You can even set a flag in your ssh config to have the files compressed to save a little transfer time.

You can get a SCP client from the creator of putty for windows.  If you have SSH installed on a linux system it has SCP functonality all ready.  To SCP from a Linux/UNIX host.

 scp [options] [[user@]host1:]filename1 ...  [[user@]host2:]filename2

eg if I wanted to scp from my local machine to my server yarak I would use the command.

scp file1.txt mike@yarak:/home/mike/files

scp is the command
file1.txt could be either a binary file or an ascii file
mike before the @ is the user name
yarak after the @ is the server which could be a local server on your lan.  You can even use a qualified domain name or ip to SCP to also.
: is to seperate the location you want to send the file to
/home/mike/files is the directory I want to send file1.txt to on the remote server

If you are not in the current directory of the file you want to send you need to put the whole file path.

Hope this helps.

---

### Post by MJN on 2006-01-26
That's not quite right, but you're along the right lines. :) 
 
SCP is indeed essentially a secure version of the *copy* command, which uses SSH to encrypt the session, however it is not akin to FTP and indeed no substitute for it. Rather it offers a limited subset of its functionality.
 
I was referring to running FTP over SSH, usually termed *secure *FTP. You mentioned the Putty suite, that does also include a Secure FTP client (PSFTP).
 
Cosmix, I am recommending SSH not only for its secure file transfer capability but I'm sure you will inevitably have the requirement to actually login remotely to a shell on your Linux box so that you are not just restricted to the manipulation of files via FTP. With SSH you'd be able to do this securely which opens up the capability of stopping/starting services, editing files in situu etc. And, believe it or not, the configuration setup and running of an SSH server is a lot easier than doing likewise with an FTP server! (It only uses a single port for a start and so is far more firewall-friendly than FTP - FTP was not designed with firewall limitations in mind).
 
Mathew

---

### Post by CosMix on 2006-01-26
Hey Mathew,

i know about ssh and its one of the essentials in linux environment i presume....but i didnt know that by using ssh u can transfer data as well...ive tried the scp command and it works fine...'cept the slow speeds i was getting (was it because the comp is old and does not allow large amounts of data being transfered fast?).anyway this ssh file transfer does solve my problem up to some point...the fact is: i want to set up a linux box (by default with ssh of course ;D) and enable linux and windows users by my choice to upload or download files. any suggestions what should i use or at least a pointer in which direction should i look for the answer. uve been of great help so far...i mean...being at disposal is a BIG thing nowadays where everybody is giving u that f**ing FAQ indication...anyways...thnx for the hints so far...and do not give up on me :D im still struggling on my own while im posting these replies,

Gorazd :D

---

### Post by LordHunter317 on 2006-01-27
[QUOTE=MJN]SCP is indeed essentially a secure version of the *copy* command, which uses SSH to encrypt the session, however it is not akin to FTP and indeed no substitute for it. Rather it offers a limited subset of its functionality.[/quote]Actually, save for the inability to list, it's featureful enough.
 
> I was referring to running FTP over SSH, usually termed *secure *FTP.Except you're wrong there.  SFTP is not FTP over SSH.  The on-wire protocol is not the same.

If you only want FTP and you already have it setup, looking at FTPS (FTP/SSL) might be worthwhile, but only if you have a real IP address, or can forward all your ports, or do binat.  You cannot proxy FTPS presently.

---

### Post by MJN on 2006-01-27
Points taken. Although saying SCP is 'featureful enough' does of course depend on what features you're after.. ;) Aside from listing files, which you've already stated, I personally value the ability to move/delete files not to mention the session-aspect of SFTP with the associated level of interactivity that this brings. Those requirements can hardly be considered radical.
 
The bottom line is that Cosmix *hasn't* got FTP set up (it can be a bu66er so this is no slight at him) and this, coupled with the fact that SSH access will likely be equally as valuable as being able to up/download files, I still think the best course of action would be to set up an SSH server and use SFTP for the file transfers (and, yes, I *do* mean SFTP in the proper sense as you've highlighted ;) ).
 
Would you agree that's the easiest way forward, and biggest bang for the buck?
 
Cosmix, in light of the above I would recommend checking out the OpenSSH suite - [http://www.openssh.com/]("http://www.openssh.com/") - dead easy to install via your package manager and, I seem to recall, the default configuration/installation works relatively securely and feature-rich 'out of the box' so you'll be up-and-running in no time.
 
Mathew

---

### Post by CosMix on 2006-01-29
A quick one,

thnx for the effort Mathew, i hope i'll be of such assistance to u some day...
...atm im goin snowboarding but ill check on the said above ASAP.
thnx again and have a nice day,

Gorazd

---

### Post by MJN on 2006-01-29
You're welcome, do let us know how you get on (or not!).

Enjoy the 'boarding!

Mathew

---

### Post by Peter76 on 2006-01-29
If all or some of the boxes you connect from are linux/unix; also have a look at the sshfs package; this is a client side tool that allows you to securely mount drives over an ssh tunnel

---

### Post by CosMix on 2006-01-31
argh %^#$#@$@^$ 

im gettin nowhere here...my old ubuntu box just went bizerk....erm...it's closed all ports....what could that be? ive checked under etc/hosts.allow and .deny, but there werent any entries. erm as far as it concerns for the ftp server...i just cant cope with it...read some dozen manuals online...tried configuring in any way i possibly could...no results...erm...would someone be a lil' more specific when addressing to a linux newbie pls :cry: . basiclly what i want to do is: set up a ftp server which will be accessible by both linux and windows users who would be able to upload and download (regitered users of course). 2nd, i would like to control this linux box with remote desktop. how and by which means....i do not know, yet. Anyways, Mathew, if u still have the 'balls' to help me ;)  ...go on n do it.

Gorazd

---

### Post by MJN on 2006-02-01
As I said, install OpenSSH instead! Trust me - it'll be more secure out-of-the-box and, just as important, it'll work!! I can't see any advantage with you continuing down the FTP route, particularly given the grief it can cause (not insurmountable but not really worth the effort).
 
Naturally, we'll offer advice on the OpenSSH front too but I'm confident you probably won't need it!
 
Mathew

---

### Post by CosMix on 2006-02-03
Hey,

i dont understand some things but im sure i do understand some...
anyways, ive tried to set up vsftpd on my other ubuntu machine...this time via xserver and synaptic manager...and the configuration was easy....it even works! \\:D/ without problems!...i dont know what's the matter with that old comp of mine...mebbe its coz its antique? hehehe anyways...thnx for persistance...and for good will in givin' me the clues. Im sure ill be back with more questions as i walk further down the path known as linux console :-D

---

### Post by CosMix on 2006-02-17
Hey,

I's been a  while since my last reply...and actually there werent needed any. I came here just to say ive succeeded in setting up a ftp server + vnc remote desktop. But all this on a machine with xserver running. Anyways, i suppose its better to start somewhere then being stuck at one point. Thnx again to u Mathew, for encouraging me and all the effort.

Gorazd

---

### Post by MJN on 2006-02-17
You're welcome, and well done for getting there!
 
That's one of the beauties of Linux - getting somewhere which you would have otherwise expected to be easy can often take ages and a whole load of head scratching... If you persevere through the times when the temptation to jack it all in is high then when you pop out the other side the feeling of achievement is invariably worth it!
 
Take, for example, setting up a printer. In Windows you'd just plug it in and it would likely work (might even have to pop a CD in) - where's the fun in that?! ;) Bring on Linux, knee deep in configuration files, hours on Google and a few forum posts later and the pleasure of actually seeing a page pop out of the printer is worth the effort! As for getting ink on that page, well, one step at a time!! :) 
 
All the best,
 
Mathew

---

### Post by CosMix on 2006-04-19
Hey Mathew,

ive set up a ftp server and its working without any probs....the thing imma gonna ask now is where should i enable server to server transfer ?

thnx m8,

Gorazd

---

### Post by MJN on 2006-04-19
What exactly do you mean by 'server to server trasnfer' - can you elaborate on what you're trying to?
 
Do you mean, for example, making backups of one machine to another?
 
If so, I'd suggest using **rsync** and, if you'll forgive my steering away from FTP again (can you tell I'm not a fan?!), it runs over SSH too.
 
Mathew

---

### Post by LordHunter317 on 2006-04-19
[QUOTE=MJN]I was referring to running FTP over SSH, usually termed *secure *FTP. You mentioned the Putty suite, that does also include a Secure FTP client (PSFTP).[/quote]SFTP is not FTP over SSH, nor nothing like it.

---

### Post by MJN on 2006-04-20
Have you been on the funny juice again LH? We've already been through this - indeed you said the same thing back in Post #9 on Jan 27th and I agreed...
 
..or are you just short on arguments at the moment? ;)
 
Mathew

---

### Post by LordHunter317 on 2006-04-20
No, it's simple as if you're going to post incorrect statements, I'm going to correct them.  This one is addmittely minor, but still important, because people get eaisly confused between FTP, SFTP, and FTP/SSL (esp. when it's called FTPS)

---

### Post by MJN on 2006-04-20
Ah... so it's the latter!

That's exactly my point - you'd already highlighted the differences between all these variations of similar themes... I'm just wondering why you decided to do it again?! Notwithstanding the fact that you make a valid point, is there any particular reason you waited 3 months to make it?!

Perhaps you need your own sub-forum where we can all drop in from time to time to play... ;)

Mathew

---

### Post by LordHunter317 on 2006-04-20
Because I am indeed on drugs, apparently.  I don't know, I swear I didn't see my own previous post before.  I think my Internet connection is playing tricks on me, or the stress really is finally affecting my sanity.  Your pick, and my apologies.

---

### Post by MJN on 2006-04-20
Fair enough... no probs.

Coming back on topic, it might help if CosMix could elaborate on what he's trying to achieve... My FTP knowledge is limited (having switched over to, and I hesitate to say, something involving file transfers over SSH! ;)) so someone else will have to take the reins for these 'server to server transfers' ...

Mathew

---

