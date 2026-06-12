---
title: "a hosting account, please"
date: 2008-04-17
forum: The Cafe
---

### Post by ruibernardo on 2008-04-17
Don't know how to ask for this...

I'm hosting a website ([nonetdebs.homeip.net]("http://ubuntuforums.org/showthread.php?t=572819")) in my personal computer with my personal internet connection. Basically it allows offline users to download packages they want to install from the repos, including all dependencies and without listing packages that are installed on the offline computer.

Now I need a free hosting service to host it. I would continue to host it here, but now I've developed a new feature to make the files in /var/lib/apt/lists/*Packages available to the offline user (developed, but still to commit due to this problem). That feature will make available to the offline computer all the packages that he can find in the repositories he have set up. Then the user can use Synaptic (File > create download script) or apt-get (--print-uris) to list the files and then download them from elsewhere (more info: [http://ubuntu.wordpress.com/2005/09/22/upgrade-install-ubuntu-on-slow-internet/#comment-54908](http://ubuntu.wordpress.com/2005/09/22/upgrade-install-ubuntu-on-slow-internet/#comment-54908)).

I can't make this happen here in my computer ATM. Although the website have only kind of 10 users per day (~500 total), the upload from my computer of 20 MB (or 6 MB if compressed) of data would be a pain (64 KB/s upload connection), specially if I'm using the internet and 2 or more users using nonetdebs tried to download the *Packages files.

I really would appreciate (and certainly many offline users would too) if some kind soul would supply a hosting account.

The ideal host account for this:
- An Ubuntu (or Debian) server (or with apt-get installed). I will use apt-get just to run "--print-uris" as a normal user - no need of sudo/root account);
- Generated locales (optional, but makes easier to users to understand "apt-get" errors);
- 500 MB minimal (+1GB ideal) to store the website (drupal 5) and the status files of the users.
- Be able to keep "nonetdebs.homeip.net" as the website name, until I buy or get some "decent" domain.

The website is not expected to have high traffic volume, but with a faster connection "apt-get update" will run faster and the upload of the /var/lib/apt/lists/*Packages" files (compressed in a bzip tar archive) would be easier.

Any help appreciated :)

---

### Post by tgm4883 on 2008-04-17
Not trying to thread crap, but wouldn't this work better as a standalone program that can download from the repos?

Sounds like you need the entire repo as well for it to work.

---

### Post by timcredible on 2008-04-17
there are a lot of hosting sites that will give you 300gb of storage and 3,000gb of data transfer a month for $6/month.  the free ones are very limited in storage and data transfer, but they're out there too, a google search should return many pages.

---

### Post by ruibernardo on 2008-04-17
Hi tmg, thanks for the reply. 

The website is like a web interface for apt to the offline users. The users upload their /var/lib/dpkg/status file so an "apt-get --print-uris" is executed knowing which packages are installed on the target. This prints the packages (from ubuntu repositories, or others) the user needs.

The user can/will be able to set the sources.list he wants (as long as no gpg key is needed, gpg key can be added if requested).

So no mirror/repos is needed.

---

### Post by sanus|art on 2008-04-17
Try here:
[http://www.000webhost.com/](http://www.000webhost.com/)

But free hosting (any) can be a mess sometimes.

---

