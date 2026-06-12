---
title: "Windows 7 cant find my Ubuntu Server 14.04 LTS in &quot;network&quot;"
date: 2015-02-01
forum: Server Platforms
---

### Post by johan23 on 2015-02-01
I have recently installed Ubuntu Server 14.04 LTS Trusty Tahr on my server. I have a HP Proliant Microserver Gen8 with 2 HHD, one 500 GB and one 6 TB. I have installed the OS on the 500 GB and mounted the 6 TB as /home. I am a complete newbie when it comes to servers and Ubuntu so please keep that in mind.

I followed this guide on youtube: [https://www.youtube.com/watch?v=9jdbwlg0QFc](https://www.youtube.com/watch?v=9jdbwlg0QFc)

I did everything exactly the same (although he installed a earlier version of Ubuntu Server) apart from creating my plex folder in /home/plex, which I also put in Samba.

Now, I cant find my server under "Computers" on my laptop, running Windows 7 Professional. It did show up at one point, but then I could not access the folder. Got the error message 0x80070035. I can ping my server through CMD successfully. I cannot access the server through explorer either by typing its IP-no into the address field. I guess the trouble has something to do with Samba? Or Windows? 

I appreciate all the help I can get. Thanks

---

### Post by DennisFolsom on 2015-03-06
4 weeks and no replies?  Ouch!

I may soon be dealing with a similar problem.  I am migrating to a new dual-boot PC with Ubuntu 14.04 LTS on the linux side.  My first attempts at samba file sharing under 14.04 did not quite work.  I moved on to using USB drives to migrate my files.  Eventually, though, I want to be able to serve files to my wife's laptop, which runs Windows 7.

I'll be researching other sources of help.  If and when I get mine up and running, I hope to check back on this thread.

---

### Post by Mark Phelps on 2015-03-06
> 4 weeks and no replies? Ouch!Well ... your post reads like a Windows problem .. and this is NOT a Windows forum.

You might try asking in a Windows 7 forum -- suggest [http://www.sevenforums.com](http://www.sevenforums.com)

---

### Post by MAFoElffen on 2015-03-06
<mark, you feeling okay?>
I didn't look at the Youtube... Mark's correct in that I try not to answer Windows questions on a Linux forum... but I don't think it's specifically a Windows problem. More likely just an SMB problem. For a Windows machine looking in Network places, that looks for smb shares. SAMBA Server (other's, but that is the main most likely, and most popular) is what we use in Linux to do smb sharing.

Having said that, I can proudly attest that Linux, using Samba, does SMB shares better and more reliably that Win Server, thus the likelihood why you did what you did. So lets make sure you have all the pieces there and configured correctly.

So I assume you installed SAMBA server services and am trying to connect to those services correct? If not, then easiest would be
```

sudo tasksel

``` 
Check the "samba" checkbox, then the install button...

If you did... then the next step would be to configure the samba conf file. The three section most important are the workgroup name, the order the services and protocols are provided and the definition of the shares.

My recommendation to you is to post your /etc/samba/smb.conf/ inside [ code ] tags...

>>>*** Note to a MOD >>> Please move this thread to the Server section so it can get the exposure it needs.

---

### Post by DennisFolsom on 2015-03-07
johan23, are you still with us?

As for my own situation, I have found some of the other resources on Samba, but haven't yet had time to give it another serious try.  I may open another thread when I do. 

Thanks, MAFoElffen, for your constructive input.

I gotta get my post count up to where I can update my profile.

---

### Post by DennisFolsom on 2015-03-08
I now have my Samba sharing and access from Windows 7 mostly sorted out.  Getting everything in the same Workgroup was one of the keys.  Here are the two resources that I used has "how-to's":
[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)
[http://www.7tutorials.com/how-access-ubuntu-shared-folders-windows-7](http://www.7tutorials.com/how-access-ubuntu-shared-folders-windows-7)

Maybe they would be helpful to johan23, if you are still following the thread.

---

