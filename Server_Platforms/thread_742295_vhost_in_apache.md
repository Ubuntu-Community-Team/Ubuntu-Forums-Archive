---
title: "vhost in apache"
date: 2008-04-01
forum: Server Platforms
---

### Post by leg on 2008-04-01
I want to set up apache and have virtual hosts set up on it for local dev work. Now I have been using Gentoo for a while and it appears that the set up is a bit different here. Before I would have a .include file in a directory vhost in the /etc/apache2 dir. In that file I would define my <Directory> sections and the names  I used also needed to be added to my /etc/hosts file. It seems that I now have toi use a directory called /etc/apache2/sites-available and create a file per vhost in there. These files should include the equivalent <Directory> section for the vhost it is meant to apply to. Do I still need to add the hostname to hosts? I believe there is a command to run after that to activate them. Is this correct?

While I am here I will quickly ask a second related question. I have a partition that contains what used to be my /var partition. Is it ok to simply mount this over my current /var or are there other differences I need to be aware of.

Thanks in advance.

---

### Post by leg on 2008-04-03
Ok I seem to have figured this out now and am currently mounting my /var partition  in my file system. I did have to check across with the /var directory Ubuntu was using and make sure that all existing files were in place before I did this but it all seems to be working so far.

---

