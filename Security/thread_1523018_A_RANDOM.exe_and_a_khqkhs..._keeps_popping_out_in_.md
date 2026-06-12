---
title: "A RANDOM.exe and a khq/khs/... keeps popping out in my desktop"
date: 2010-07-03
forum: Security
---

### Post by adwraj on 2010-07-03
I don't know what is the reason but I was setting up samba on my Ubuntu 10.04 desktop. I wanted to share my printers and files to a laptop using windows and I manage to get Samba working to share files.
Suddenly, I see this [Random].exe and a khq file keep popping in my desktop. I did add desktop into my share, so I thought the virus is moving from the windows computer but I was wrong. I cleaned up the whole windows computer and tested it with my windows desktop. So I turned off the windows computers and just left my Ubuntu on and those .exe and khs files keep coming back even if I delete them.

I've removed wine, and also replaced my firefox profile according to what I see in one post which talks about the same thing.
Please help me out, coz i don't want to reinstall everything all over. Thanks.

---

### Post by adwraj on 2010-07-03
I don't know what is the reason but I was setting up samba on my Ubuntu 10.04 desktop. I wanted to share my printers and files to a laptop using windows and I manage to get Samba working to share files.
Suddenly, I see this [Random].exe and a khq file keep popping in my desktop. I did add desktop into my share, so I thought the virus is moving from the windows computer but I was wrong. I cleaned up the whole windows computer and tested it with my windows desktop. So I turned off the windows computers and just left my Ubuntu on and those .exe and khs files keep coming back even if I delete them.

I've removed wine, and also replaced my firefox profile according to what I see in one post which talks about the same thing.
Please help me out, coz i don't want to reinstall everything all over. Thanks.

---

### Post by Yarui on 2010-07-03
I really doubt this behavior is coming from a virus.  If it was, it would be one of the most useless and unintrusive viruses I have ever heard of.  It sounds totally harmless, just annoying.

If it keeps coming back I'm sure it's probably something being caused by odd behavior in some software, whether it is software on the linux machine or the windows machine is hard to say.  You could try unplugging the linux machine from the network entirely to see if it continues with this behavior.  If it keeps coming back even when not on the network it would surely be something happening on your machine.

---

### Post by prshah on 2010-07-03
> **adwraj said:**
> Suddenly, I see this [Random].exe and a khq file keep popping in my desktop.

I do believe that inspite of your best efforts, the error files are being created on your Windows computer. 

If you decide to post the exe and khq/khs files here ([g]zipped, and with appropriate WARNINGS IN BIG BOLD LETTERS), then I can run it in a VM to check if Wine can possibly be affected.

Also, please execute these commands on your desktop (Please modify as appropriate, eg, do not use "*.exe" if you have other exe files in your Desktop directory)```
ls -l *.exe *.khq *.khs
rm -v *.exe *.khq *.khs
sleep 10 && ls -l *.exe *.khq *.khs
```

Everything at your own risk, so please apply due caution.

---

### Post by Yarui on 2010-07-03
> **prshah said:**
> 
Also, please execute these commands on your desktop (Please modify as appropriate, eg, do not use "*.exe" if you have other exe files in your Desktop directory)```
ls -l *.exe *.khq *.khs
rm -v *.exe *.khq *.khs
sleep 10 && ls -l *.exe *.khq *.khs
```Everything at your own risk, so please apply due caution.
You should probably give at least a short explanation of what this does in case the OP doesn't know, since it's generally a bad idea to run commands that you don't understand.  I'm a little unsure why you are instructing to list the exe khq and khs files, remove them, wait 10 seconds and then list them again... I am mainly confused about waiting 10 seconds, are you wanting to see if the files return within 10 seconds?

---

### Post by adwraj on 2010-07-03
Hi prshah,
I've attached a pair of them which. 1 exe and 1 khq. By the way, the khq files are not extensions, its just khq, khw or khs. So that command is not so usefull, and the files don't return in 10 seconds, they take a few minutes before they come back. I've turned of all the computers in the network, which means its only me and the internet.

And Yarui, thanks for understanding. I do understand a little about the command. Hope I can remove this annoying problem so that I don't need to like reinstall everything over again.

By the way, the files keep coming in pairs and if i don't delete the khq. The next pair will be an .exe and khw and so on.

Update : The files only comes when the internet is on, it feels like its being downloaded since it takes time for the second file to pop out.

---

### Post by prshah on 2010-07-03
> **adwraj said:**
> I've attached a pair of them which. 1 exe and 1 khq. 

You've probably missed a Windows machine somewhere. Try [http://www.symantec.com/security_response/writeup.jsp?docid=2008-102011-5014-99&tabid=3](http://www.symantec.com/security_response/writeup.jsp?docid=2008-102011-5014-99&tabid=3) for removal instructions for this malware.

The exe file posted is a Win32 executable and will not run in linux without WINE (And _may_ not work with WINE either!)

Please check the Symantec instructions and post back.

In the meantime, I plan to run it in a virtualized VM of XP and Linux, and see what happens...

---

### Post by adwraj on 2010-07-03
> **prshah said:**
> You've probably missed a Windows machine somewhere. Try [http://www.symantec.com/security_response/writeup.jsp?docid=2008-102011-5014-99&tabid=3](http://www.symantec.com/security_response/writeup.jsp?docid=2008-102011-5014-99&tabid=3) for removal instructions for this malware.

The exe file posted is a Win32 executable and will not run in linux without WINE (And _may_ not work with WINE either!)

Please check the Symantec instructions and post back.

In the meantime, I plan to run it in a virtualized VM of XP and Linux, and see what happens...


I've already read all this before posting. I have a Windows 7 on the same machine I have Ubuntu and another laptop with Windows XP. I tried that Symantec instructions on both the computers and found nothing in my registry.

---

### Post by OpSecShellshock on 2010-07-03
Is there any removable storage media attached? I've read the description of the worm and it appears to infect shared drives and removable media.

That probably won't do much to explain why it comes back after waiting a few minutes, though.

On Windows systems it appears that a successful installation will include rudimentary backdoor capabilities. It messes with a lot of stuff. Machine of origin was almost certainly the XP box in your case. I'd reinstall the OS for that one. As for the others, I'd format any removable storage media using a known-clean machine.

If the files are being replaced only when an internet connection is present then it may be the case that a process is checking in with a remote host to confirm the presence of the files. That would be bad, but no reason to panic. Check your messages log to see where it's coming from and which process is being used.

---

### Post by adwraj on 2010-07-03
Ok guys,
I don't think you're gonna believe this, but after all this time of messing around, I think I found the problem. I've even turn off all the internet, LAN or anything but it still comes back.

I used the synaptics package manager and did a complete removal of wine 1.2, and thats it... No more files popping out, even with internet or any windows machine on. I can't actually believe this myself but yes that solved the problem..

prshah: i think it worked with wine.

OpSecShellshock: Yea i tried checking my pendrive and my hardisk but I don't see any autoruns, or even any unknown files. By the way, how do I check my messages log to see where it's coming from and which process is being used ? I would like to know how to do that, in case of any other problems i encounter.

And thx guys for helping me out.

---

### Post by cariboo on 2010-07-03
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by adwraj on 2010-07-03
> **cariboo907 said:**
> Please don't create multiple threads on the same subject, I have merged your two threads.

Hi, I'm sorry about the multiple threads. I posted twice because I can't find the option to change the prefix.
When I posted as lubuntu, nobody replied but when I posted as ubuntu I got some replies.
Can you please guide me how to change the prefix of a thread ? Thanks.

---

### Post by cariboo on 2010-07-03
Have some patience, remember that we are all volunteers here, if no ones answers your question after 24 hours, then you can bump the thread, no need to create an other one. I think the majority of us here don't pay attention to prefixes, so don't worry about it.

---

### Post by adwraj on 2010-07-03
OK sure... Thank you cariboo907.

And just for the update. After I reinstalled wine, the files don't pop out anymore. Everything is back to normal.

---

