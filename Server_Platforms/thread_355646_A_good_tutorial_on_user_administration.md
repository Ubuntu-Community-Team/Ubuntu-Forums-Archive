---
title: "A good tutorial on user administration?"
date: 2007-02-07
forum: Server Platforms
---

### Post by intrepidus on 2007-02-07
I'm trying to set up one of my machines to allow multiple users access to it to allow them to do their Ruby on Rails projects as part of class. I'm running Ubuntu Server, no GUI. Is there some sort of decent tutorial on user administration out there that can point me in the right direction on how to limit their rights enough to run rails, but not give them too much to break things?

---

### Post by elst on 2007-02-07
The usual way to do this kind of thing on Web servers is to enable the Apache module ModUserDir. If users then create a "public_html" directory within their home directory it automatically becomes a Web site.

I haven't done this with Rails, so I don't if there are any Rails-specific quirks. There may be some more information on hosting on the Rails Wiki.

---

### Post by Brazen on 2007-02-07
> **intrepidus said:**
> I'm trying to set up one of my machines to allow multiple users access to it to allow them to do their Ruby on Rails projects as part of class. I'm running Ubuntu Server, no GUI. Is there some sort of decent tutorial on user administration out there that can point me in the right direction on how to limit their rights enough to run rails, but not give them too much to break things?

Just let them create their rails app in their home directory.  Rails is just a program that they run that creates a file and folder structure and many other nifty things.  A regular user by default is able to run the rails application.  The user will just need to do this in their home directory:```
rails appname
```

You will then need to alias into Apache the public folder under the rails application.  Something like this in your default site:```
alias /appname /home/username/appname/public
```

Then of course create a suitable <directory> section according to the RoR directions.  The student will be able to do whatever he wants to his rails app in his home directory and then access it through [http://servername/appname](http://servername/appname)

---

