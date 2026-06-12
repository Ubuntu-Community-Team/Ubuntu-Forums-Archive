---
title: "Web Server in School environment"
date: 2007-09-26
forum: Server Platforms
---

### Post by boombah on 2007-09-26
Hi, I am after a little help. 

I want to set up an internal web server at my school so that students can learn php, mysql and publish websites. Now due to various financial contraints it is left to me to try and accomplish this with no money and an old machine. 

I want each student to have their own account, be able to create their own php code and mysql databases. The students also need to be able to publish these sites on their own accounts, something like server/~studentname. Is this possible? If so how? 

Any help would be appreciated

Cheers.

---

### Post by jakev383 on 2007-09-26
Certainly. It also boils down to how much work you want to put into it. You could setup (by hand) each user's directory and databases, or you can use a control panel - there are free ones.  Look at ISPConfig, and also check out HowToForge - they have some how-tos for setting up Ubuntu (and others like CentOS and Fedora) for a multi-website environment.

---

### Post by boombah on 2007-09-27
> **jakev383 said:**
> Certainly. It also boils down to how much work you want to put into it. You could setup (by hand) each user's directory and databases, or you can use a control panel - there are free ones.  Look at ISPConfig, and also check out HowToForge - they have some how-tos for setting up Ubuntu (and others like CentOS and Fedora) for a multi-website environment.

Thanks for the advice. Here is what i have managed to get done today. 

1. Installed 7.04 server.
2. Installed the ubuntu desktop as i am reasonably new to Linux.
3. Installed Webmin.
4. Set up 2 user accounts and virtual servers which work.

The problem now is that the only way i could work out how to setup virtual hosts was to create a new hostname for each user. This is not what i intended. So now instead of server/~student1 i have student1.

So first of all how do i change that?, and secondly, how do i assign a user access to their virtual server and nothing else?

Thanks

---

### Post by jakev383 on 2007-09-29
[QUOTE=boombah;3433676]Thanks for the advice. Here is what i have managed to get done today. 

1. Installed 7.04 server.
2. Installed the ubuntu desktop as i am reasonably new to Linux.
3. Installed Webmin.
4. Set up 2 user accounts and virtual servers which work.

The problem now is that the only way i could work out how to setup virtual hosts was to create a new hostname for each user. This is not what i intended. So now instead of server/~student1 i have student1.

So first of all how do i change that?, and secondly, how do i assign a user access to their virtual server and nothing else?
[QUOTE]

server/~student1/ will just be a directory under the webroot. I don't remember what it is under Ubuntu, but under Redhat based distros it's /var/www/html and to have student1 I would just:
```
 mkdir /var/www/html/~student1 
```
And then you would be able to access their folder at server/~student1
Now as far as locking access to just their folder.....  Are you talking about giving them FTP access and locking them to their folder, or SSH access and locking them to their folder?

---

### Post by HermanAB on 2007-09-29
Note that there is also something called Virtualmin, which is an add-on to Webmin, specifically for virtual servers on Apache.

Cheers,

Herman

---

### Post by threeten on 2007-09-30
Perhaps you are wanting per user web directories.  Users can create web sites in their own home directory.  It also gives you a degree of control.


[http://httpd.apache.org/docs/2.2/howto/public_html.html](http://httpd.apache.org/docs/2.2/howto/public_html.html)

---

