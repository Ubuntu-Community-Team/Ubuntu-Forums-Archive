---
title: "Apache2 installation not working after uninstalling it."
date: 2007-06-12
forum: Server Platforms
---

### Post by ddevore on 2007-06-12
I am configuring a server using 6.06 lts 64bit. I was having problems with the Apache2 installation so I uninstalled the whole thing. I then noticed that it looked like it left some files around so I went through and manually deleted the apache2 files that didn't seem they should be there. I figured I would reinstall everything and all would be right with the world. I have now solved my problem on another computer and want to reinstall the (LAMP) setup and start over. When I went to install apache2 though it only installed the docs (/usr/share/doc/apache2). I have tried everything I could think of with apt-get and have had no luck getting it to reinstall. 

What do I need to do? I do not want to install it all manually because I like the way that the package installed it and I want to keep as much as I can standard Ubuntu for upgrading. 

Please help. 

Dru

---

### Post by juantao on 2007-06-13
How attached to this installation are you? You could save what's important and do a clean (with format) reinstall. Or... Apt-get will abide by the --force directive as in <apt-get --force -yes install apache2> but here's what the man page says about that "--force-yes
          Force yes; This is a dangerous option that will cause apt to continue without
          prompting if it is doing something potentially harmful. It should not be used
          except in very special situations. Using force-yes can potentially destroy your
          system! Configuration Item: APT::Get::force-yes.

Might be best to wait for a better answer. Anybody?

---

