---
title: "gnucash install failed"
date: 2006-12-05
forum: Repositories &amp; Backports
---

### Post by dsimpson on 2006-12-05
I tried to install gnucash via synaptic. There is no listing under applications or icons signifying the install was completed. I received the following message following the download:
  The following problems were found on your computer
  E: msttcorefonts: subprocess post-installation script returned
     error exit status 1

I then tried to install via terminal by inputting:
sudo apt-get install gnucash
received the following error message:

Reading package list...done
Building dependency tree...done
Gnucash is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional space will be used.
Setting up msttcorefonts (1.2Ubuntu3)...
warning: /usr/share/A11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatability". This is no longer the case, but they are
still available from third parties.

You are free to download and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file or package format.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name
 andale32.exe: no such file or directory

All done, errors in processing 1 file(s)
dpkg:error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

I don't really know what this all means or how to fix it, would appreciate any help that can be sent my way, Thanks

---

### Post by biffta on 2006-12-06
Thats some seriously strange error messages you got there, think the first thing you should do is share with us your /etc/apt/sources.list file.
> Gnucash is already the newest version.
What happens if you just type gnucash from the command line?

---

### Post by dsimpson on 2006-12-06
/etc/apt/sources.list, just brought up a message "permission denied".
Opening up and running Gnucash from terminal started the program but gnucash would close when I closed terminal. I tried saving from terminal but saved account gave following message when I tried to open it, "XML parsing error: prefix not bound to a namespace. It tries to open the program in a firefox window. I don't want to have to run my programs from a terminal each time, hope something here will help define the problem and a solution is found. Thanks for the feedback.

---

### Post by Klarsin on 2006-12-10
Can I interject? I'm having the same problem. Synaptics says that gnucash is installed, and I found these files in usr/bin:

Gnucash
Gnucash-config
Gunucash-env
Gnucash-make-guids
Gnucash-run-script

However, gnucash does not show under the application menu

I did a terminal install "apt-get install gnucash" and got this:

Reading package lists... Done
Building dependency tree... Done
gnucash is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 63 not upgraded.

This did not open gnucash.

Then I did this:

me# gnucash

GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.

Don't know what this is, however gnucash did open! Wow! But as you described it quits when you close the terminal.


Is there something missing in the install package (upgrage version maybe) Would this be considered a "broken install?"

Likewise, I'd like this to appear under the applications.

---

### Post by Klarsin on 2006-12-10
> **Klarsin said:**
> .

Then I did this:

me# gnucash

GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.

Don't know what this is, however gnucash did open! Wow! But as you described it quits when you close the terminal.



Oh, I think my root session timed out?

I guess gnucash dosnt need a root to open...right?

---

### Post by califman831 on 2006-12-25
hi,
I am also experiencing the same program getting Gnucash to load from the desktop. I
Managed to start it from the terminal as a previous poster mentioned but am
getting this message


Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",

I also created a launcher which does pull up previously saved accounts, which i created.

---

