---
title: "Domain names without apache"
date: 2011-12-02
forum: Server Platforms
---

### Post by Nouman on 2011-12-02
Hey guys,

The question I have is how would I host domain names on my box (11.10) without using Apache and virtual hosts?

thanks!

---

### Post by volkswagner on 2011-12-02
OK,  I'll bite.

Why don't you want to use Apache2?

In my opinion the big three web servers would be:

Apache2, [lighttpd]("http://www.lighttpd.net/") and [Nginx]("http://nginx.org/").  An honorable mention may go to[ Cherokee]("http://www.cherokee-project.com/").  There are others I'm sure. 

Before anyone can offer an opinion.  It may be best to describe your requirements and your dislikes for Apache2.

---

### Post by CharlesA on 2011-12-02
I'm going to bite too. Apache is one of the most used web servers around.

---

### Post by Nouman on 2011-12-02
I should elaborate!

I work with PHP and love apache; however, this won't be a LAMP setup.

I'll be running node.js on the box, so apache won't be needed.

EDIT: I've used to get setup: [http://apptob.org/](http://apptob.org/)

---

### Post by CharlesA on 2011-12-02
Interesting way to run a web server.

Might want to check on their [site]("https://github.com/joyent/node/wiki"). They are on IRC too.

---

### Post by Nouman on 2011-12-02
Setting up my domain through Godaddy, and running Node on port 80 works for a single domain setup.

Since that's all I need running for now, I'm set. (Though if anyone knows how to support multiple domains, please let us know!)

I will definitely take a look into the node community for similar questions.

thanks!

---

