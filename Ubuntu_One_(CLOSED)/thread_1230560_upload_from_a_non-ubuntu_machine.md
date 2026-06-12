---
title: "upload from a non-ubuntu machine?"
date: 2009-08-03
forum: Ubuntu One (CLOSED)
---

### Post by martin saint martin on 2009-08-03
is this doable?  say i'm at school, working on a windows machine, i've got to go, so i save my work, but i lost my flash drive and need to work on this project at home.  can i upload my saved work from the said windows box at school?  i'm hoping that if my home machine was running while i was at school it(my home desktop) and ubuntu one would sync-> my saved project will be there waiting for me to pick up where i left off at school.

---

### Post by cariboo on 2009-08-03
The simple answer is no. There is no Windows client **yet**.

I read your post before reading [this]("http://ubuntuforums.org/showthread.php?t=1229797") thread. If you os of choice is not supported, you can roll your own.

---

### Post by Mia1990 on 2009-08-03
no Windows client yet and i hope that no one make's one.There is dropbox and a few other that will work on both leave ubuntu one for ubuntu.

---

### Post by zekopeko on 2009-08-03
web interface?

---

### Post by martin saint martin on 2009-08-04
i'm not looking for a client software for windows (the thought of it makes me sick), i was wonder if via the web interface i could upload a file or two.

---

### Post by cariboo on 2009-08-04
You need the client to create an Ubuntu One directory otherwise it won't work, I just tried it on XP running in a vm.

Ubuntu One is similar to Dropbox and other services, you need a client for your os in order to use the service.

---

### Post by martin saint martin on 2009-08-04
> **cariboo907 said:**
> You need the client to create an Ubuntu One directory otherwise it won't work, I just tried it on XP running in a vm.

Ubuntu One is similar to Dropbox and other services, you need a client for your os in order to use the service.

i assume that you tried it via the web interface.
i find it odd that i can download to a winbox, but only upload from a linbox.
this is supposed to be *cloud-computing*, right?

please for give me if i sound ungrateful, i truly appreciate the generosity that is ubuntu one and ubuntu in general.(i hope that didn't come out sarcastic sounding, i've been having trouble with that my whole life.)

---

### Post by James Henstridge on 2009-08-04
We don't have immediate plans to port the client to other platforms, but the client is free software so others are free to have a go.

The intended way to access your files on systems that don't have the client installed is through the web interface.  If that doesn't work for you, then please file a bug report at [https://bugs.launchpad.net/ubunet/+filebug](https://bugs.launchpad.net/ubunet/+filebug).  Describe what you were trying to do, and include information about any error messages received.

I don't know if much testing has been done with Windows based browsers, but Firefox will likely give the least troubles since it acts essentially the same on Windows and Linux.

---

### Post by GoldenSun on 2009-08-04
Uhh i uploaded a bunch of music files from my windows machine to it.  I have my linbox sitting at home with the client running.  I'm at work and I uploaded through the web interface.  

I'm not sure what you guys are talking about as I can do it from windows 2000.

---

### Post by zekopeko on 2009-08-04
> **martin saint martin said:**
> i assume that you tried it via the web interface.
i find it odd that i can download to a winbox, but only upload from a linbox.
this is supposed to be *cloud-computing*, right?

please for give me if i sound ungrateful, i truly appreciate the generosity that is ubuntu one and ubuntu in general.(i hope that didn't come out sarcastic sounding, i've been having trouble with that my whole life.)

You can upload files by using the web interface from any platform (Win/Mac/Lin). 
Install the U1 client on your Ubuntu box and set it up (you have to do this to get access to the web interface). 

Work on your documents at school and once you are finished upload the via the web interface to U1 service. Your Ubuntu box will be auto synced with the new files. 

You can test this by uploading a file from your Ubuntu box via web interface and watch it get synced by the U1 client.

Hopes this helps.

---

### Post by cariboo on 2009-08-04
I see where I went wrong, I didn't set up sharing.

---

### Post by Inevitable Glitch on 2009-09-20
It seems to me, though I haven't tried it, that you should be able to do that through the web interface.

I have a dualboot set up with ubuntu and XP and I have access to the Ubuntu One folder when I am in XP.  In theory, I think I should be able to drop files into that folder when in XP and have them sync when I boot into ubuntu.  Haven't tried it yet, but I will and then come back and let you know how it goes.

Edit:  Ok, I logged into XP and tried it out.  I first copied two small files into my ubuntu one folder through XP, then I logged into the web interface using Firefox on XP and was able to upload another file through that.  I then tried it with Internet Explorer 7 on XP.  Although I was able to log in to the web interface using IE7, I wasn't able to upload or download any files, and the page didn't appear to load completely.  I could see a list of what files I had though.  After doing that, I rebooted back into ubuntu and the client instantly uploaded the files that I had placed into the ubuntu one folder using XP, although it hasn't yet downloaded the ones I put in using the web interface, they show up in the web interface so I expect it will sync them soon enough.

So, in answer to the original poster's question: Yes, you can upload to ubuntu one from Windows using the web interface and firefox.

---

