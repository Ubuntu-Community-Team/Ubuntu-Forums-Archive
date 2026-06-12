---
title: "Personal Cloud Server"
date: 2014-04-11
forum: Ubuntu Cloud and Juju
---

### Post by dhavalbbhatt2 on 2014-04-11
Hello all,
I have a need, for which, I don't have a solid solution and am hoping that folks in here can help. Also, excuse me if this is not where this post belongs and thanks to anyone who responds.

I have the need to be able to access my files from anywhere. Of course a cloud based service like Dropbox should suffice, however, I am in no mood to hand my data to them. As a result, I am looking at a couple of options: 1) Buying NAS which will give me everything that I need, however, that will be costly and 2) Use my existing PC (it has Ubuntu 12.04LTS 64bit on it), add a new NAS HDD on it and use that as a cloud server. I am leaning towards the second option given that I already have most of the hardware. I have heard about ownCloud, and how to turn a PC into a cloud server ([http://www.tecmint.com/install-owncloud-to-create-personal-storage-in-linux/](http://www.tecmint.com/install-owncloud-to-create-personal-storage-in-linux/)), however, I am worried that this option would be insecure.

I guess the questions that I want to ask are - 
1) Is the method documented in the link, secure?
2) If not, what changes do I need to make to ensure security? (security for me will include making the webserver secure as well as encrypting the files on the cloud server)
3) Are there other options to make this really simple (using the current hardware that I have)?

Any insights will be greatly appreciated.

Thanks,
DB

---

### Post by jdeca57 on 2014-05-07
Security is always an issue, and nobody can give you a clean insurance. Still, I just installed Owncloud on a server for internal lan use with [http://sharadchhetri.com/2014/01/16/how-to-install-owncloud-6-in-ubuntu-13-10-server/](http://sharadchhetri.com/2014/01/16/how-to-install-owncloud-6-in-ubuntu-13-10-server/) and that seems bona fide since it points to the opensuse builds that Owncloud recommends. It's less hassle than the manual way with wget that your link suggests. And it provides a link to the ssl installation that's necessary in order to be more secure: actually your link stops at the http. The url I provided is not complete, it's more like a path to follow. Of course references to 13.10 should be replaced with 14.04, for instance. I wouldn't recommend an installation that's open to the net unless you're quit confident about your ability to administer said security...

---

