---
title: "Setup Apache?"
date: 2007-05-25
forum: Server Platforms
---

### Post by intrepid_geek on 2007-05-25
(Ubuntu Server, 7.04)
(Also posted in Absolute Beginners Forum, sorry, I didn't see this section on Servers)

Ok I found where my web page files are/should be located.
Now is there an easy way to get them there from my workstation? Somehow, creating and editing them in vi doesn't appeal to me. Maybe SAMBA? SFTP?

If someone could just point me in the right direction I'll figure it out, but I don't know the most secure way to do this. In other words, how do the real WebAdmins do it?

---

### Post by rickyjones on 2007-05-25
I would personally install an FTP server and use that to upload the files.

---

### Post by gombadi on 2007-05-25
My opinion -

Use rsync to update the web site files

i.e.
Have  the web site on your workstation the same layout (directories/files) as the live site.
Run the following command
```

rsync -e 'ssh -x' -av /local/path/to/web/site/ user@server:/path/to/live/site

```

As you change the web site then only the changes will be sent through to the server. Just be carefull about file ownership and permissions on the server (the web server only needs to read the files not own them)

To make life even easier you can setup passwordless access so it does not ask for a password each time.
Also you could setup and alias by adding the following to your .bashrc file in your home directory
```

alias uw='rsync -e \'ssh -x\' -av /local/path/to/web/site/ user@server:/path/to/live/site'

```

Then when ever you want to update the site just open a terminal and type "uw"

---

