---
title: "sudo:  I can't get it to run multiple commands.  example within..."
date: 2008-03-05
forum: Server Platforms
---

### Post by s2cuts on 2008-03-05
Good day all,

I need to get this to work, however I'm having difficulty with sudo.  Take a look.

```
$ echo <su_password> | sudo -S { echo <smb_password>; echo <smb_password>; } | smbpasswd -s <smb_user>
```

It needs to be scripted, and sudo doesn't seem to understand the commands that follow it even though they work as root.  Again keep in mind that the passwords need to be passed in like this because this needs to be scripted.  If someone can get this to work I'll be their best friend for life...

---

### Post by Oldsoldier2003 on 2008-03-05
> **s2cuts said:**
> Good day all,

I need to get this to work, however I'm having difficulty with sudo.  Take a look.

```
$ echo <su_password> | sudo -S { echo <smb_password>; echo <smb_password>; } | smbpasswd -s <smb_user>
```

It needs to be scripted, and sudo doesn't seem to understand the commands that follow it even though they work as root.  Again keep in mind that the passwords need to be passed in like this because this needs to be scripted.  If someone can get this to work I'll be their best friend for life...

try inserting sudo before smbpasswd

---

### Post by koenn on 2008-03-05
or leave out the sudo's and run the script itself as root / with sudo

---

### Post by s2cuts on 2008-03-05
Ok, after playing a bit more I've gotten the following to work:

```
echo [password] | sudo -S smbpasswd -s [smbuser] < [password_file]
```

Is there any way of fooling smbpasswd into taking a redirection from something other than an actual file on the file system?

Thanks for any help.

---

### Post by s2cuts on 2008-03-05
> **koenn said:**
> or leave out the sudo's and run the script itself as root / with sudo

Yes, interesting suggestion, which would probably work.  This, however, is going to be part of a cgi script.  First of all, is it even doable with Apache?  And secondly, would it be wise to run a web app as root, even if it's for your LAN only?

Thanks.

---

### Post by koenn on 2008-03-05
I think the problem with that is that you need to repeat the password, with [enter] after the 1st one. Maybe there's an escape sequence for that, like \n in C or &(some-ascii-number); in html. Then 1 echo statement would be enough and you could probably pipe that. 
(along the lines of : echo pass \n pass | smbpasswd .... )
maybe look at some bash documentation ? 


here's a workaround using a temporary file :
(I leave out the sudo, I assume you run the script itself with sudo)
```

# replace 'pass" with the actual password
passwdfile=$(tempfile)
echo pass > passwdfile
echo pass >> passwdfile

smbpasswd -s [smbuser] < passwdfile
rm passwdfile

```

---

### Post by koenn on 2008-03-05
this might work as well :
```
smbpasswd -s [smbuser] <<EOF
pass
pass
EOF

```
it's called "here documents" (<<) and works as redirected input from a file, except that there is no file : it uses whatever is between the EOF markers as "file".

---

### Post by koenn on 2008-03-05
> **s2cuts said:**
> Yes, interesting suggestion, which would probably work.  This, however, is going to be part of a cgi script.  First of all, is it even doable with Apache?  And secondly, would it be wise to run a web app as root, even if it's for your LAN only?

Thanks.
missed your post there.

I don't know much about cgi so I don't know if it's doable. I'd feel uncomfortable running web scripts as root, I think the proper way, if it's absolutely necessary, is to separate the parts that need to be run as root, i.e. put those in a separate script that you call from within the main script (and pass values to it) - that way, your main script doesn't run as root and priviligues are dropped when they're not needed anymore, i think (might depend also on your sudo time-out)

It's also not wise to have passwords in clear text scripts - i take it you'll want to replace the smbpasswords with variables (in wich case 'here documents' may not work but the tempfile workaround would).
You might need to have your (sudo) password in the script so you depend on apache and www-data permissions and the modes/permissions on your directories to keep it hidden, right ?
maybe someon with server-side scripting experience can shed some light.

---

