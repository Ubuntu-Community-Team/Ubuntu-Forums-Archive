---
title: "where is command line?"
date: 2011-12-03
forum: System76 Support
---

### Post by kzhu on 2011-12-03
I have installed Ubuntu 11.10 on my USB hard drive.  Everything seems OK.  But I have a couple of questions. 1)The first item on the task menu (on the very left) is "Installation".  I think my Ubuntu installation is completed.  Why would we need it? 2)I cannot find the standard Unix command prompt.  I need it to execute some commands, such as adduser, chmod, etc.  3)It seems I cannot write files to /etc/var/www folder because of permission issues.  How do I solve it?

---

### Post by bluexrider on 2011-12-03
To open a **Terminal** do as follow:     
                      
                                
[LIST]
[*]                      	    Choose Applications &#8594; Accessories &#8594; Terminal; 	  
[*]                      	    Or press **Alt**+**F2** 	    and type **gnome-terminal**. 	  
[/LIST]

---

### Post by cbennett926 on 2011-12-03
I have used a USB to install Ubuntu as well and I had the same issue with the "Install" on there as well. I went in and removed the "install" program within the repositories and that took care of the issues.

---

### Post by drewbenn on 2011-12-04
ctrl-alt-t should also open a Terminal.

What are the current permissions on /etc/var/www?  You could see them with 'ls -al' (e.g. "ls -al /etc/var/www" and look at the permissions and owner for ".") then fix the permissions problem by either changing the owner (chown) or the permissions themselves (chmod) (you may want to read the man page for each of them, e.g. "man chown" to see the list of arguments and a brief explanation of what they do).

What are you trying to do that requires changed permissions for /etc/var/www?  Are you sure you want to change them?  It should be pretty rare to need to change permissions or owners in /etc (or /var if you meant /var/www).

Oh, and you can add users through a GUI.  I don't know where it is in the latest Ubuntu, but in Debian Squeeze it's: System | Administration | Users and Groups; I imagine it's near there for you.  You should be able to change permissions (chmod) from inside Nautilus (the file manager), too.

---

