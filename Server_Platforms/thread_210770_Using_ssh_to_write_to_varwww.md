---
title: "Using ssh to write to /var/www"
date: 2006-07-07
forum: Server Platforms
---

### Post by brickhead20 on 2006-07-07
I'm trying to set up my Ubuntu desktop system to write to a laptop system downstairs, into the /var/www folder for apache2. How do I set the permissions so I can effectively open the folder and write to it from the desktop?

Any help would be appreciated :) 

Rich

---

### Post by coach-x on 2006-07-07
If you want to copy the files securely through ssh you could use rsync.

rsync -azv -e ssh ./file/path user@remote_system:/var/www

---

### Post by brickhead20 on 2006-07-07
OK cool thanks, and that won't worry about permissions? Say if I want to edit html and php script files though directly, through a graphical interface such as nautilus, just because its easier, is there a way of using this graphically?

---

### Post by kewldude606 on 2006-07-07
What I do when I want to write to /var/www is open up a terminal and do sudo su, then I enter in cp /file/editing/locally /var/www/on/remote/comp.  Every time I make a change, I just save the file locally and hit up-enter in the terminal.

I imagine you aren't concerned about secure connections because it is in your network?

You can also press Alt-F2 and do sudo <app> and then you can write directly to the comp.

---

### Post by brickhead20 on 2006-07-07
Nah Im not too worried about security, but security rocks anyway, so preserving it is always helpful just incase. So it won't mind me at all writing to the other computer? Thats cool. Thanks. Any other methods?

EDIT: It won't let me use the first method because it says:

cp: accessing `/media/Webserver': Permission denied

I have the /var/www mounted as /media/Webserver using sshfs. I'll try setting the folder to being owned by me on the server.

---

### Post by Slim Odds on 2006-07-07
> **brickhead20 said:**
> Nah Im not too worried about security, but security rocks anyway, so preserving it is always helpful just incase. So it won't mind me at all writing to the other computer? Thats cool. Thanks. Any other methods?

EDIT: It won't let me use the first method because it says:

cp: accessing `/media/Webserver': Permission denied

I have the /var/www mounted as /media/Webserver using sshfs. I'll try setting the folder to being owned by me on the server.

scp works just fine:
```
scp localfiles user@remote:/var/www/
```

---

### Post by brickhead20 on 2006-07-07
I found that by setting the permissions of /var/www so it was owned by me allows me to write to the folder. That's fine really. Yeah, I never tried scp, I'm sure it may work fine also. I find the CLI quicker on the server (and more fun :) ), but just because I'm a lazy fag its nice to have a graphical interface on the desktop for quick editing, and to have a nice clear mount for command line editing. The only thing that concerns me in setting the owner to my username, is security. Is it really an issue?

Nonetheless I can now edit the files from the command line using ViM! YAY!

Thanks for the help and quick responses everybody!

---

### Post by Randomskk on 2006-07-07
Having /var/www chown'd to your username is fine, it's what most people do.
The permissions should be something like 755, right? That means that you (the owner) can read+write, and anyone else can just read.

---

### Post by brickhead20 on 2006-07-07
Yeah, its 755 I think. I just set it with gksudo nautilus :)

---

### Post by nagilum on 2006-07-08
Have you considered using WebDAV? Quite easy to setup with Apache and you don't have to worry about permissions since Apache itself writes the files to /var/www with proper owner and permissions. Nautilus can connect to WebDAV and you can easily put your website online with Drag&Drop etc.

---

### Post by brickhead20 on 2006-07-09
Cool, I'll check it out. This connection via ssh is good fun though :p I'll add it to my overgrowing box of tools.

---

