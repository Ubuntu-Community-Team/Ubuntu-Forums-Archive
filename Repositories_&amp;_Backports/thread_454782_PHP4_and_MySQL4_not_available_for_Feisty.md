---
title: "PHP4 and MySQL4 not available for Feisty"
date: 2007-05-25
forum: Repositories &amp; Backports
---

### Post by Peter Mount on 2007-05-25
Hi

This is s serious problem for me and I'm seriously thinking of changing back to Fedora because of this. I used to be able to install PHP4 with MySQL4 with the aid of [this]("https://help.ubuntu.com/community/ApacheMySQLPHP"). Feisty wont let me do this.

My web host only has PHP4 and MySQL4. They wont upgrade to PHP5 and MySQL5 for another year. Don't tell me to change web hosts because I have clients hosted with them and a change would mean an increase in hosting fees.

I"m going to install Fedora on my third hard drive today as I know there are instructions [here]("http://www.transcendingthought.com/content/view/31/42/") on installing PHP4 and MySQL4 on any version of Fedora. I've seen some page on installing PHP4 on Feisty as a CGI but it didn't show how to install MySQL4.

I love using Kubuntu and it seems so much more stable than Fedora. I just believe this decision to dump PHP4 and MySQL4 at this time is a serious mistake as a lot of Web Devlopers like me really need it for compatibililty testing. 

Can somebody just tell me if there is any plan to make both PHP4 and MySQL4 available for Feisty in the repositories and when?

---

### Post by paparucino on 2007-05-26
> **Peter Mount said:**
> Hi

Can somebody just tell me if there is any plan to make both PHP4 and MySQL4 available for Feisty in the repositories and when?
As you can see here, [http://downloads.mysql.com/archives.php?p=mysql-4.0](http://downloads.mysql.com/archives.php?p=mysql-4.0), mysql4 has been discontinued and the binaries are no more available.

---

### Post by Peter Mount on 2007-05-26
> **paparucino said:**
> As you can see here, [http://downloads.mysql.com/archives.php?p=mysql-4.0](http://downloads.mysql.com/archives.php?p=mysql-4.0), mysql4 has been discontinued and the binaries are no more available.

MySQL4.1 is still here at [http://dev.mysql.com/downloads/mysql/4.1.html]("http://dev.mysql.com/downloads/mysql/4.1.html").That's what I was using in Kubuntu Edgy and I don't see why they don't have that available in the repositories with PHP4.x for Feisty.

Seeing as Fedora 7 is just around the corner I'll wait until that comes out to see if there is a feasable way to get MySQL4.1 with PHP4.x working on Feisty. If there isn't I'll be getting my hands on Fedora 7.

---

### Post by toppy on 2007-05-27
I guess I should have done some reading before I upgraded to Feisty.  Is there a downgrade script?! :)

---

### Post by Peter Mount on 2007-05-29
I just found out that a version of XAMPP will help me with this. It is [here]("http://sourceforge.net/project/showfiles.php?group_id=61776&package_id=60248")

I read I should look at XAMPP version 1.4.16

I hope it does work as I'd prefer to stay with Kubuntu. I'll report back after I've tried ti.

---

### Post by toppy on 2007-06-01
Any reports Peter?

---

### Post by mrcbrown on 2007-06-02
I'll reply for this one - works, MySQL 4.1.x and with this command:

/opt/lampp/lampp php4

You can enable PHP4 vs. the stock v5 that ships with it. The instructions are here:

But grab the file from the above link (if you need PHP4/MySQL4) and you'll be good to go:

[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

If your new to Linux (just in case) instead of typing "su" in step one, simply add "sudo" in front of the second command:

sudo tar xvfz xampp-linux-1.4.16.tar.gz -C /opt

Start up LAMP:

sudo /opt/lampp/lampp start

Change to PHP4:

sudo /opt/lampp/lampp php4

And you should be good to go, if your on the same machine simply open your browser to 127.0.0.1 or localhost, or if from another networked machine the IP of the Ubuntu box.

Good Luck!

---

### Post by Peter Mount on 2007-06-03
> **toppy said:**
> Any reports Peter?

Hi

I followed mrcbrown's post and it works (although I just used the standard way of extracting a file and using Konqeror by typing "kdesu Konqueror" in the terminal to copy the files to the /opt directory from my user home directory)

It now says I have the following running:

PHP Version 4.4.0
MySQL 4.1.14

Sorry about my delay in reporting. mrcbrown has shown the way to make PHP4.x and MySQL4.x work on Feisty and I'm glad. I was thinking of changing to Fedora 7 but (K)Ubuntu has shown itself to be more stable than at least the previous versions of Fedora.

Have fun

---

### Post by toppy on 2007-06-04
Thank you very much mrcbrown.  That worked without a hitch and is easier in a way.  I like the option of switching from php4 to php5 support.  Very nice.

---

