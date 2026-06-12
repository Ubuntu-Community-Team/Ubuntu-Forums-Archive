---
title: "Var WWW write permisions"
date: 2013-11-05
forum: Server Platforms
---

### Post by Blix775 on 2013-11-05
So I've been trying to have writting permission to the /var/www while still having www-data being able to do whatever it wants to the files in that place. I would like to use things like wordpress along with my own code. The ubuntu server pdf manual suggest the following commands to let you do that:
```
sudo chgrp -R webmasters /var/www
sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws
"{}" \;
```
Now. I would like to know how to create a group for both my account and www-data to have acces to that folder. Or add my account to the group that www-data is on. So my question is how do I do this since I just replace "webmasters" with my username (which is a group also) and that just leaves www-data out of the group. I would like to know which option is better and how to do it. Thanks for the help.

---

### Post by stmiller on 2013-11-05
I would suggest just adding your username to the group www-data.

It is best to use what is already the ubuntu / apache / nginx default (re: www-data).

```

sudo chown -R www-data:www-data /var/www/

```

And add your user to that group:

```

sudo gpasswd -a jsmith www-data

```

---

### Post by Blix775 on 2013-11-06
> **stmiller said:**
> I would suggest just adding your username to the group www-data.

It is best to use what is already the ubuntu / apache / nginx default (re: www-data).

```

sudo chown -R www-data:www-data /var/www/

```

And add your user to that group:

```

sudo gpasswd -a jsmith www-data

```
I have not done anything yet so I'd like to know if the first command is irrelevant in my case since www-data should own or have access to do whatever it wants in that folder. And the second command is adding me to the group www-data is on? Thanks for the help.

---

### Post by Lars Noodén on 2013-11-06
The user and group www-data exist to provide an unprivileged user for the web server.  Using it for anything else breaks this privilege separation and risks introducing trouble.  So no www directories should be owned by it and certainly no users members of the group.  

If the folder has mode 775 or 755 or 555, that is enough to provide read access to www-data and that is enough to serve web pages from that directory.

---

### Post by Blix775 on 2013-11-06
The problem I have is that I want to place the files directly into that folder since I'm learning HTML5, PHP and other stuff. I don't know how to ftp files up into my own machine (if that makes any sense) or any other way of getting the files there. It's the first time I'm setting up my own server for my own code. Normally I just use pre-made pages. So how can I place the files on the directory safely? I'm guessing adding my user into that usergroup.

---

### Post by Lars Noodén on 2013-11-06
If you are the only person using that machine then you can change ownership of the directory:

```

sudo chown dennisvalencia /var/www

```

That will give you write permissions to add web pages or PHP scripts. 

Otherwise if you are sharing with one or more people what you did in #1 is the right way.  Then all that's left is to add your account to that group "webmasters"

```

sudo gpasswd webmasters  --add dennisvalencia

```

That will add you to the group and will take effect next time you log in.

---

### Post by Blix775 on 2013-11-06
> **Lars Noodén said:**
> If you are the only person using that machine then you can change ownership of the directory:

```

sudo chown dennisvalencia /var/www

```

That will give you write permissions to add web pages or PHP scripts. 

Otherwise if you are sharing with one or more people what you did in #1 is the right way.  Then all that's left is to add your account to that group "webmasters"

```

sudo gpasswd webmasters  --add dennisvalencia

```

That will add you to the group and will take effect next time you log in.
That's what I want to do. I'm the only one using this machine but www-data has to be able to write to it. I need to create the group before adding anyone into it because I don't think webmasters exists by default. Or does it?

edit: OK. I get it. That first command created the group and added www-data to it. I'll give it a try asap. Thanks.

---

### Post by Blix775 on 2013-11-07
> **Lars Noodén said:**
> If you are the only person using that machine then you can change ownership of the directory:

```

sudo chown dennisvalencia /var/www

```

That will give you write permissions to add web pages or PHP scripts. 

Otherwise if you are sharing with one or more people what you did in #1 is the right way.  Then all that's left is to add your account to that group "webmasters"

```

sudo gpasswd webmasters  --add dennisvalencia

```

That will add you to the group and will take effect next time you log in.
OK. I just did the three commands found in the pdf but changed "webmasters" with www-data and then I added myself to the www-data with that last command. It seems to be working fine since I tried phpbb to see if it could write to the folder and it can. Thanks everyone. Also, if there's any drawback to what I did, let me know.

---

