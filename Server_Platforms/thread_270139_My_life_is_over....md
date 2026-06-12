---
title: "My life is over..."
date: 2006-10-02
forum: Server Platforms
---

### Post by McHenry on 2006-10-02
I am completing the setup of my first Ubuntu server and last night trasnferred the files from a XP box to the /tmp directory on the server using WinSCP

It was a lot of data so I let it transfer overnight.
In the morning no errors on the XP box, source dir gone as it was a move not a copy however on the Ubuntu box there is nothing !!!!

the user account that WinSCP uses is admin which is non root.

Please help as I am really in it deep here...

---

### Post by anodizer on 2006-10-02
Oh, bad news. The contents of the /tmp folder are deleted after a reboot.

---

### Post by pppetter on 2006-10-03
...Hence the name "tmp"

I wouldn't really say that your life is over, there's alot of tools out there that you can use to recover those files, either on your Windows machine, or the ubuntu one. You might not it all back, but it actually works better than you might think!

I once did a mistake(at least I think that it was me, don't remember) and accidentially removed my ntfs partition. I installed the package testdisk on my ubuntu partition and used photorec(included in testdisk) to recover alot of different types of files.

And that's just one of the tools available...

---

### Post by bigken on 2006-10-03
you could restore the windows box to a ealier date see if your files restore

the best data recovery software I have used is [ontrack]("http://www.ontrack.com/easyrecoverydatarecovery/") data recovery

---

### Post by merkur2k on 2006-10-03
so I see you've learned why sysadmins always use copy instead of move? :D

---

### Post by hkgonra on 2006-10-03
For sure !!! I ALWAYS copy first and then and only then do I delete the old copy if I don't want it in the original place.

---

### Post by seansco on 2006-10-19
freeundelete is a good and free program for undeleting files under windows

---

### Post by Lord Illidan on 2006-10-19
He's dead, Jim.

---

### Post by Anonii on 2006-10-19
Am I the only one who smiled seeing the emo-ness of this thread?

---

### Post by cogsprocket on 2006-10-19
I was about to tell him not to jump but after hearing the story I smacked myself on the forehead and considered egging him on.

You should be able to recover your files as long as you cautious about the method you use to recover them.  I wouldn't try a system restore as that may not do the job depending on where the files were.  In fact it could give you even more problems.  Instead try a reputable data recovery tool.  If you have to pay, do it.  It's worth it to make the investment if it means that you won't have to live with a huge mistake.

---

### Post by Lord Illidan on 2006-10-19
> **cogsprocket said:**
> I was about to tell him not to jump but after hearing the story I smacked myself on the forehead and considered egging him on.


*THUD* Ok, who pushed him?

---

