---
title: "How do you logout from ubuntu server"
date: 2006-11-26
forum: Server Platforms
---

### Post by peter@kkvs on 2006-11-26
In Ubuntu server there is no logout or logoff command (as opposed to other distros).

So if one wants to logout from the server there does not appear to be any way of doing so other than a reboot.

Surely it does not require this !

---

### Post by junglepeanut on 2006-11-26
exit?
I log out with logout and exit which ever suits my mood at the time...I wonder why yours is not.

---

### Post by breezyfox on 2006-11-26
> **peter@kkvs said:**
> In Ubuntu server there is no logout or logoff command (as opposed to other distros).

So if one wants to logout from the server there does not appear to be any way of doing so other than a reboot.

Surely it does not require this !

Hi
There is command use can use to logoff. Use any of the folowing in terminal.
1. Logout
2. CTRL+alt+del --------it will reboot
3.To shutdown immediately--- Sudo shutdown -h now, you need to switch off power.
4. Sudo shutdown -r now --- will reboot

Hope this helps

BZ

---

### Post by Lucho77 on 2006-12-07
I use 'CTRL+D' to log out.

---

### Post by Porrly on 2006-12-07
> **breezyfox said:**
> Hi
There is command use can use to logoff. Use any of the folowing in terminal.
1. Logout
2. CTRL+alt+del --------it will reboot
3.To shutdown immediately--- Sudo shutdown -h now, you need to switch off power.
4. Sudo shutdown -r now --- will reboot

Hope this helps

BZ

Alternatives are:

3) halt

4) reboot

Both of these are equivalent to what breezyfox posted (IE they operate IMMEDIATELY.

You could also use 'init 0' or 'init 6' (I think 0 is shutdown and 6 is reboot! :-? )

---

### Post by Wim Sturkenboom on 2006-12-08
Why tell TS how to reboot or whatever if he/she just wants to logout :confused:

---

### Post by tturrisi on 2006-12-08
> **Wim Sturkenboom said:**
> Why tell TS how to reboot or whatever if he/she just wants to logout :confused:
Perhaps the poster was unaware of the existence of those additional commands.

---

