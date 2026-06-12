---
title: "Creating sandboxes for apache2"
date: 2010-02-21
forum: Server Platforms
---

### Post by ajcrites on 2010-02-21
I already have apache2 up and running, and everything is cool, but I would like to be able to create a sandbox outside of public_html for my own server site.  I want it to be user.localhost, for instance.  Then, the site will be built from whatever is in /home/user/httpd.  I set up a server alias *.localhost, and I have a folder ~/httpd , but it doesn't work.  I know there has to be another step in there.

While I'm at it, I would also like to use mercurial (already installed as well) to manage the site between ~/httpd and /var/www.  Would I have to do anything other than create the repository, checkout to ~/httpd, and when I'm ready, pull and update as root in /var/www ?  It just seems too easy.

Thanks for the help.

---

