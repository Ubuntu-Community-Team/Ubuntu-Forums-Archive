---
title: "Rebooting with PHP (or other web)"
date: 2009-09-25
forum: Server Platforms
---

### Post by Databit on 2009-09-25
I've been trying to figure this out for 2 days now. I'm trying to reboot a server using a web link. 
I've tried things like
shell_exec('echo "PASSWORD" | sudo -S reboot');

which won't work because apache isn't a sudoer so I've tried

shell_exec('echo "PASSWORD" | sudo -S -u userwithssudoer reboot');

which doesn't work because it runs as the right user but that user can't run reboot without sudoing... so

shell_exec('echo "PASSWORD" | sudo -S -u userwithssudoer sh reboot.sh');
where reboot.sh contains:
echo "PASSWORD" | sudo -S reboot

And that doesn't work either (I'm not sure why not)

Any ideas how to make this happen?

---

### Post by hessiess on 2009-09-25
Being able to reboot/shut-down a server with a web link is a very bad idea from a security point of view (who needs to DDOS you when you can just power down the server ;) ).

Howeaver you could add the command with nopasswd to the sudoers file.

---

### Post by rnodal on 2009-09-25
Set the setuid flag of the script to the user than can perform the action and from your php script call that other script.

-r

---

### Post by volkswagner on 2009-09-25
I am sure not the only one wondering why?  Unless it was a windows server....  ;)

If I absolutely needed to restart my sever via a browser I would use Webmin.

I must agree it seems to be a tremendous security hole installed.

---

### Post by abaden on 2009-09-25
Don't keep your root password in any file on your system. 

I think your best bet is to setup a script and put it in the sudoers file. You can read more about that file [here]("https://help.ubuntu.com/community/Sudoers"). Of interest to you will probably be the command alias section, though you should read the whole thing, since screwing up sudoers can screw up your system. There's even an example that seems to pertain to you under "common Tasks".

Good luck, and let us know what you find.


Alex

---

### Post by Databit on 2009-09-28
Thanks all. I'm going to try out the sudoer file idea which should do it.
The why is that this is a vendor provided piece of equipment and they recommend for a particular set of issues to reboot the servers. Looking to automate it and provide a web link to our help desk so they can reboot it. I know this isn't the best security wise but our chance of someone trying to DOS this particular server is slim to none plus the admin page will have decent authentication to it.

---

