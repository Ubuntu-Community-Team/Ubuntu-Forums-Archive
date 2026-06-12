---
title: "Internet problems Gateway MT6705 laptop"
date: 2007-08-29
forum: Washington DC Team - US
---

### Post by ericsaxalto on 2007-08-29
I have successfully installed Ubuntu on my Gateway MT6705 as the primary operating system, however, I cannot get any internet connection - even with an ethernet connection.  I have wireless at the house and the computer detects wireless, but I get a message saying "Firefox can't find server".  I went into the Networking and punched in the IP address but nothing has changed.  Any suggestions?:confused:

---

### Post by KevinCole on 2007-08-29
> **ericsaxalto said:**
> I have successfully installed Ubuntu on my Gateway MT6705 as the primary operating system, however, I cannot get any internet connection - even with an ethernet connection.  I have wireless at the house and the computer detects wireless, but I get a message saying "Firefox can't find server".  I went into the Networking and punched in the IP address but nothing has changed.  Any suggestions?:confused:

If you know the IP number of a web site (as opposed to the IP name), you could try entering that into your browser to see if that part is working okay.  For example, **[COLOR="Red"]http://69.147.114.210/[/COLOR]** should take you to Yahoo.  If that works then the problem sounds like a DNS error.  Look at the contents of **[COLOR="Red"]/etc/resolv.conf [/COLOR]**.  It should have a couple of lines in it that begin with:

[INDENT][FONT="Fixedsys"]**nameserver**[/FONT][/INDENT]

followed by an IP number.  Since you are setting your IP number manually, I'm assuming you will also know the IP addresses of your DNS nameservers.

Let us know how it goes.

---

### Post by ericsaxalto on 2007-08-29
KevinCole,

Thanks for the suggestion.  I entered the IPaddress and it poped up with a message that says: "Firefox doesn't know how to open this address, because the protocol (htp) isn't associated with any program." I tried it with a couple different IP addresses and it didn't work.  If you have any other thoughts I'm happy to try.  Thanks again!

---

### Post by KevinCole on 2007-08-29
> **ericsaxalto said:**
> KevinCole,

Thanks for the suggestion.  I entered the IPaddress and it poped up with a message that says: "Firefox doesn't know how to open this address, because the protocol (htp) isn't associated with any program." I tried it with a couple different IP addresses and it didn't work.  If you have any other thoughts I'm happy to try.  Thanks again!

Try again.  It looks like you had a typo in your address.  Use [COLOR="Red"]**http**[/COLOR] not **htp**.  (Maybe you can copy and paste it from my previous message to avoid typing mistakes.)

---

### Post by dinomite on 2007-08-30
If **KevinCole** then it would help us to have more information.  If you could capture the output of the command **ifconfig** and, perhaps using a USB thumb drive, post it here that would be useful.  To make a file with the output of **ifconfig** open a terminal from the Applications > Accessories menu and type **/sbin/ifconfig > ~/Desktop/ifconfig.txt** which should result in a new file named **ifconfig.txt** appearing on your desktop.  Just post the contents of that file here.

-Drew

---

### Post by ericsaxalto on 2007-08-30
> **dinomite said:**
> If **KevinCole** then it would help us to have more information.  If you could capture the output of the command **ifconfig** and, perhaps using a USB thumb drive, post it here that would be useful.  To make a file with the output of **ifconfig** open a terminal from the Applications > Accessories menu and type **/sbin/ifconfig > ~/Desktop/ifconfig.txt** which should result in a new file named **ifconfig.txt** appearing on your desktop.  Just post the contents of that file here.

-Drew
I ran the commands that you suggested and I got the **iconfig.tx**t on my desktop, but when I opened it it was blank.  I would have put the contents in but there simply were none.  I don't know what that means.

---

### Post by KevinCole on 2007-08-30
> **ericsaxalto said:**
> I ran the commands that you suggested and I got the **iconfig.tx**t on my desktop, but when I opened it it was blank.  I would have put the contents in but there simply were none.  I don't know what that means.

OK... Go back into the terminal, and this time type:

> [FONT="Courier New"][b]sudo -i
/etc/init.d/networking restart
ifconfig
cat /etc/resolv.conf
tail -n 20 /var/log/messages[/b][/font]

See if any of that yields useful information. The above sets you up as the root user, then tries to restart the network.  You should see it give you a bit of info as it tries to do this.  Then **ifconfig** should give you the status of your network devices. **cat /etc/resolv.conf** should tell you if your DNS nameservers are set up correctly. **tail...** should look at the last 20 lines in your messages log, which is one of the better places to look when  something's going wrong with your system.  (There are several others in /var/log/ that are worth keeping an eye on.)

---

### Post by ericsaxalto on 2007-08-31
> **KevinCole said:**
> OK... Go back into the terminal, and this time type:



See if any of that yields useful information. The above sets you up as the root user, then tries to restart the network.  You should see it give you a bit of info as it tries to do this.  Then **ifconfig** should give you the status of your network devices. **cat /etc/resolv.conf** should tell you if your DNS nameservers are set up correctly. **tail...** should look at the last 20 lines in your messages log, which is one of the better places to look when  something's going wrong with your system.  (There are several others in /var/log/ that are worth keeping an eye on.)

KevinCole, I ran those commands but the terminal wouldn't register anything (any keys) once it asked for the password.  Here's what I got:
ericsaxalto@ericsaxalto-laptop:~$ iconfig
bash: iconfig: command not found
ericsaxalto@ericsaxalto-laptop:~$ /sbin/iconfig>~/Desktop/ifconfig.txt
bash: /sbin/iconfig: No such file or directory
ericsaxalto@ericsaxalto-laptop:~$

---

### Post by KevinCole on 2007-09-01
> **ericsaxalto said:**
> KevinCole, I ran those commands but the terminal wouldn't register anything (any keys) once it asked for the password.

When it asks for the password, just type it and press enter.  It won't "register" anything. When you're typing the password nothing shows up.  Just type it in anyway, and press enter.  And type carefully.

> **ericsaxalto said:**
> Here's what I got:
ericsaxalto@ericsaxalto-laptop:~$ iconfig
bash: iconfig: command not found
ericsaxalto@ericsaxalto-laptop:~$ /sbin/iconfig>~/Desktop/ifconfig.txt
bash: /sbin/iconfig: No such file or directory
ericsaxalto@ericsaxalto-laptop:~$


[SIZE="4"]i[COLOR="Red"]**f**[/COLOR]config.[/SIZE]  (You missed the "f")

---

