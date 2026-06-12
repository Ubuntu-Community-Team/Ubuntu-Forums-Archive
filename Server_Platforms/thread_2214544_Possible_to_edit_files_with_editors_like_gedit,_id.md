---
title: "Possible to edit files with editors like gedit, idle, on headless server thru ssh"
date: 2014-04-01
forum: Server Platforms
---

### Post by mobidoy2 on 2014-04-01
I connect to a headless server (Dropplet from digital ocean) thru ssh, I also did a bookmark in nautilus to browse it.

I would like to be able to edit files in /usr/share with my local gedit, idle or other editors. Problem is that I get an error saying I do not have rights to edit those files when I try to save.

Is there anything that can be done other then either use vim on the server or saving in my home in server and copying those file back where they belong ?

---

### Post by nerdtron on 2014-04-01
> Problem is that I get an error saying I do not have rights to edit those files when I try to save.
That's because you are logged in as a normal user and you want to edit system files. If you edit file on the command line with "sudo", that means you are editing as root. So either you logged in using nautilus as root (which is not recommended) or you add permission to you user to edit the files.

> Is there anything that can be done other then either use vim on the  server 
If you find vim too hard to use, try using nano to edit files.

> or saving in my home in server and copying those file back where  they belong ?
Actually this is what happens when you edit the files using gedit. It copies the file locally, then upload. The only difference is that is it does this on the background.

---

### Post by mobidoy2 on 2014-04-02
Since it is only a pre-prod server, what I did was to add my user to root group on the server, changed the rights on the folders I need to tweaks to 775. When done, I will change group and owner to 755 and owner to root:root

---

### Post by msandoy on 2014-04-05
Easy sollution would be to install nautilus on the server, this will also install the required GUI files. after installation, ssh -X into the server, and run sudo nautilus. You will run a local instance of nautilus, displayed on your screen.

---

