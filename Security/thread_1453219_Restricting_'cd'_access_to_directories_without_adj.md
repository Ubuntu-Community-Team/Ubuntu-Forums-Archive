---
title: "Restricting 'cd' access to directories without adjusting permissions"
date: 2010-04-13
forum: Security
---

### Post by dgohn on 2010-04-13
Ok I am not sure if this is possible, so here I am.


Is there a way to restrict users that are logged into the shell via SSH/Telnet/SFTP from using the 'cd' command to move into certain directories, yet not use the chmod command to do it?  For instance, restrict users logged in from accessing the /var/www/ folder but have it still accessible using a web browser.  Also, would this defeat the purpose since they could just wget from it if its still web accessible through a browser?

Thanks!

---

### Post by dgohn on 2010-04-13
*bump*

---

### Post by cdenley on 2010-04-13
I believe what you want is to jail the user in a chroot. This is really easy with SFTP, depending on what version of ubuntu you have.
[http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

For shell access, you would actually need to set up a chroot environment, which is basically a whole OS within your OS.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

Don't use telnet. It's just ssh without any encryption.

---

### Post by dgohn on 2010-04-13
Thanks for the great ideas.  This sounds like what I need to do.  It does however look like it will still allow the files to be retrieved to another server using wget.  Is this true?  If so, is there a way to prevent that without hindering the files being accessed through a browser?

---

### Post by cdenley on 2010-04-13
> **dgohn said:**
> Thanks for the great ideas.  This sounds like what I need to do.  It does however look like it will still allow the files to be retrieved to another server using wget.  Is this true?  If so, is there a way to prevent that without hindering the files being accessed through a browser?

You mean you don't want local users to be able to access the web server? You can configure apache to disallow its own IP, but allow others. You can also use iptables to filter traffic. Seems kind of pointless if they can access the same data elsewhere, though.

---

### Post by dgohn on 2010-04-13
I have php scripts that when called in a web browser do not reveal the underlying code.  That is what I am trying to avoid.  As it stands, they can cd into the directory, open the file with nano/pico and view the code.  Or they can log into another server and just wget the file and open it that way to view the code.  That is what I am trying to avoid.  Sorry if I didn't explain my reasoning sooner, probably should have.

---

### Post by cdenley on 2010-04-13
> **dgohn said:**
> I have php scripts that when called in a web browser do not reveal the underlying code.  That is what I am trying to avoid.  As it stands, they can cd into the directory, open the file with nano/pico and view the code.  Or they can log into another server and just wget the file and open it that way to view the code.  That is what I am trying to avoid.  Sorry if I didn't explain my reasoning sooner, probably should have.

wget is the same as a browser. They both retrieve files from apache using HTTP. They both retrieve the same content in the same way. The only difference is wget doesn't display it. When retrieving content with wget, your PHP source code will not be revealed, regardless of where wget is being run from.

---

### Post by dgohn on 2010-04-13
Ahah, I guess I did not realize that.  Just tested it and you are indeed right.  I appreciate the help and I will post back when I get the chroot set up.  Thanks again!

---

### Post by bodhi.zazen on 2010-04-13
I suggest you use apparmor to restrict users when the log in with ssh.

Restricting what a user can do on a shell (via ssh) is very different form accessing a file in /var/www with wget. You would need to restrict access with wget from apache (see htaccess or similar).

---

