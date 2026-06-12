---
title: "Uploading sites on Ubuntu to web host provider"
date: 2011-10-02
forum: Server Platforms
---

### Post by Andylau on 2011-10-02
I have created a site on Ubuntu. How can I host my site on the internet through web host provider (e.g. hostgator)?
Or is there a better way of hosting my site on the internet on ubuntu?
Any help appreciated.

---

### Post by volkswagner on 2011-10-02
I have friends that are happy with HostGator.  I also have friends that are happy with GoDaddy.  There are many choices.  Just pick one within you budget and feature needs.

Once you are setup, you can FTP your content up to the host.

Are you planning on or did you already purchase/register a domain name?

If this is just a hobby site, and you don't  mind opening port 80 at home, you can host from home.  Depending on you agreement with your ISP, and if they don't block port 80 this can be a good learning task to get familiar with the components/steps to hosting.

---

### Post by Andylau on 2011-10-02
I am planning on a new domain. Should mysql or anyother stuff related to the drupal sites (but not part of file directory) be also included in the content? If yes, onto where can I upload mysql  or this type of files?

Also, can I use Filezilla to up my content to the host?

I think I will very likely host the site from home. But it seems that there are other alternatives other than port 80. Mind if I know what they are?

---

### Post by TravisZ on 2011-10-02
Yes, the MySQL data will likely need to be included. I would perhaps upload the MySQL data one (or more directories) above what is visible to the web.  It is not good practice to have .sql dumps sitting in web accessible directories.

For example:

If your public directory is /home/user/public_html i would make a new directory and upload the MySQL data to /home/user/mysql_data.

Using Filezilla should be fine and I'm guessing either FTP or SFTP would work for you.  SFTP would be the better option.

What other options are you looking for in regards to port 80?  Are you looking for different web server software other than Apache? Something like nginx?

---

### Post by Andylau on 2011-10-04
The idea of separating the .sql dumps(does it mean the file  databasename.drpl1 from phpmyadmin?) from the web accessible directories is great. I will do that definitely after creating the sites.

Found that Apache would be enough for a beginning CMS site builder. From this discussion topic, also found out there is more than 1 option (i.e. port 80) in the web server and that&#8217;s interesting. So, I want to know more and wonder what they are.

f.y.i, below the link I found some useful info abt site hosting:
[http://support.hostgator.com/articles/hosting-guide/publish-your-site/how-to-move-a-drupal-site-from-one-host-to-another](http://support.hostgator.com/articles/hosting-guide/publish-your-site/how-to-move-a-drupal-site-from-one-host-to-another)

---

