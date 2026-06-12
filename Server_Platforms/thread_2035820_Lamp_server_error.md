---
title: "Lamp server error"
date: 2012-07-31
forum: Server Platforms
---

### Post by stareling on 2012-07-31
I installed a standard lamp server on my Ubuntu distro.  I enabled the php modules, commented out the "IfInclude" block and reloaded apache2 and still, when I try to execute web pages with php in the public_html folder, I get a download prompt.  This is really stumping me, any help would be appreciated.:guitar:

---

### Post by nbetham on 2012-07-31
What ifinclude block are you refering to? In the past all I've had to do is install php5 and 'a2enmod php5' then restart apache.

---

### Post by stareling on 2012-07-31
I've done that.  I've loaded the modules, and I've enabled the public html folder.  It suddenly stopped working.  Now I've done several fixes, and none of them have worked.  I think it's a bug could.  I got it working, and it suddenly stopped parsing my php in the public_html folder.  

I simply don't want to be accessing the files by root so often.  

I had it working and it just stopped i'm going nuts.
):P

---

### Post by nbetham on 2012-07-31
Just found this thread about, I think, the same problem you're having: [http://ubuntuforums.org/showthread.php?t=1521010](http://ubuntuforums.org/showthread.php?t=1521010)

---

### Post by stareling on 2012-08-10
Thanks dude.  I think it's a bug, that link really helped.  What I did to fix it was a work around.  I changed the DocumentRoot in apache to my public html file.  Now I can program without logging in as root.  Thank vato.

---

