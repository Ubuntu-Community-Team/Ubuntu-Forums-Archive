---
title: "Remote desktop acces"
date: 2017-03-09
forum: Virtualisation
---

### Post by Jorhel on 2017-03-09
Hi,
I installed citrix for remote acces of my work desktop. When I go on my work site and click on the citrix link nothing happen.
When I look for the citrix in the list of programs and open it there is a window asking me to add a new account. I have tried putting in there the web adress of the service I'm trying to access and the window load for ever without anything more happening.
My computer is 32bit. I have talk to the work IT people but because it's Linux OS they don't know what to do....
I have checked that the firefox plug in is activated and that the pop up blocker will allow that site.
Any idea of what is going wrong? More than likely I installed the wrong version I went for the latest receiver for linux web client x86 under the debian packages.
After clicking download that prompted me to open with the sofware installer which I did.
The strange thing is if I look at the log of the software installer there is nothing installed today but citrix is there in my list of programs.
If anybody can shine some light it would be appreciated.

---

### Post by iamjiwjr on 2017-04-25
If you installed citrix version 13.5, uninstall it. Install version 13.4. It works most of the time.

---

### Post by sp40140 on 2017-04-25
Ubuntu software center is bit iffy with third party deb files.
You can confirm the install by running: "sudo dpkg -l | grep -i citrix"
If it's there, it installed fine.
If it's not there, go to the folder where you have the .deb file (typically "Downloads" folder) and run: "sudo dpkg -i <filename>.deb"
It should install it.
Once that is done, with citrix, you typically get a small .ica file when you click on the remote access icon. Make sure that that file type is associated with citrix in your browser, or just save that ica file and open with citrix manually.

Also, this is not the correct section for citrix. I think it should be moved to either networking or general help.

---

### Post by Jorhel on 2017-05-11
Thanks guys I will give it a try when I sorted my new and more urgent issues...

---

