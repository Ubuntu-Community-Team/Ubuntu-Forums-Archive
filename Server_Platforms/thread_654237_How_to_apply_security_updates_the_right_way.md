---
title: "How to apply security updates the right way?"
date: 2007-12-30
forum: Server Platforms
---

### Post by ^rooker on 2007-12-30
I'm responsible for several servers, and so far I've kept them up to date manually (compiling from sources).

Now, I'd like to use apt to apply security updates, but *only* security updates and not just "apt-get upgrade". Furthermore, I've experienced that some "security updates" break my setup (e.g. mysql update introduced some change in their DB structure, marking some tables as invalid)

I've searched the web for some informations if there is a "best practice" way of doing this, but so far I didn't come to any conclusion.


Any hints/tips?

---

### Post by p_quarles on 2007-12-30
Best way is to subscribe to the Ubuntu security announcements mailing list:
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce)

And read about security updates as they are released. You'll then be able to determine whether a given patch is necessary for the kind of server you're running, and decide whether to install it based on that.

---

### Post by ^rooker on 2007-12-30
I forgot to mention:

Even with more sources enables in /etc/apt/sources.list, how can I find out which of them actually come from security-repositories?

---

### Post by p_quarles on 2007-12-30
You can perform a "dry run" of an upgrade by doing this:
```
sudo apt-get upgrade -sV
```
That will give you verbose information about the upgrade will do without actually performing it. 

You may be able to play around with /etc/apt/apt_preferences to set up priorities for different kinds of packages, but that's not something I have much experience with.

The easy way, IMHO, is to comment out the non-security repos, and then enable them temporarily when you wish to install a new package from one of them.

---

### Post by ^rooker on 2007-12-31
About commenting out non-security repos:

I've tried that once and it ended up miserably... :(
It seemed that some dependency of a security update caused apt to think that it should remove the packages that it could not "find" (because they were in the main repos).

So I ended up with an updated apache that offered me to "download" PHP files instead of interpreting them. :)

very strange.

---

### Post by gpredrag on 2007-12-31
That should be easy to achieve, just make sure that only security repository, and not gutsu updates or proposed updates are in your sources file. That way ONLY security updates will be installed.
That said, I must add: world is not perfect. Only a week or so I was bitted by a bug introduced by security update to Linux kernel (NFS4 mounts failed, computer hungs). To be honest this is not LTS I am using. So in any case one should test updates of important services.

---

### Post by p_quarles on 2007-12-31
One other thing to keep in mind:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

You can get .deb packages for everything in the Ubuntu repositories through that site. This way, you could be as selective as you like about what patches you apply, but wouldn't need to compile anything.

Also, if your servers are all on the same network, it would be pretty easy to download the packages to a single server, and then write a script that would grab and install new packages from that server.

---

### Post by koenn on 2007-12-31
> **^rooker said:**
> I'm responsible for several servers, and so far I've kept them up to date manually (compiling from sources).

Now, I'd like to use apt to apply security updates, but *only* security updates and not just "apt-get upgrade". Furthermore, I've experienced that some "security updates" break my setup (e.g. mysql update introduced some change in their DB structure, marking some tables as invalid)

I've searched the web for some informations if there is a "best practice" way of doing this, but so far I didn't come to any conclusion.


Any hints/tips?
You might consider an LTS release - they're meant to get security patches only, IRC. Besides that :

The sollution to your problem is going to consist of several components. Here are a few things you can consider :

- you can install specific deb files with dpkg -i filename.deb. 
I believe filename.deb can also be an url so you can point to a specific file in a repo or on a web server were you collect your deb files

- to make it a bit user friendly you could do a combination of :
* run apt-get  -s upgrade (to find what packages are available for upgrade
* install packages one by one, eg with apt-get install package_name. (although dependencies will be installed as well)

- you can always check in advance where a package  will come from (and what versions are available) with 
"apty-cache policy package_name". eg 
```

~$ apt-cache policy mozilla-thunderbird
mozilla-thunderbird:
... 
  Version table:
 *** 1.5.0.13+1.5.0.14b-0ubuntu0.6.06 0
        500 http://security.ubuntu.com dapper-security/main Packages
        100 /var/lib/dpkg/status

     1.5.0.2-0ubuntu2 0
        500 http://starbase01 dapper/main Packages

```

- apt itself has a number of ways to let you install sepcific versions, from specific repo's, etc. Here's an intro : 
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version)

To manage multiple systems, you could look into apt-proxy (caches packages so you only download them once), or run a web server where you keep your own selected (or compiled) and tested packages. You can use your own web server as an apt-source for your network quite easily, or make a "partial  mirror" of the official repo's (eg the security updates repo)

---

### Post by klausthorn on 2008-07-06
thanks for the advice. I tried to automate it by shellscripting (below).
After pasting the functions into a bash shell you could run:

```
secupdate
```

to see what it would (not) do. Really update with:

```
secupdate -y
```

(if you are asked for your password each time sudo is used then it will be annoying.
 If you are not asked, it is helpful.
 It is safe to first assume that the following code will destroy your system
 and thus only use it after you have confirmed it does not.)

```
apt_upgrade_sim() { sudo apt-get upgrade -s "$@"|grep -v '^Conf' ;}
apt_install_sim() { sudo apt-get install -s "$@" ;}
apt_install()     { sudo apt-get install -y "$@" ;}
confirmed()       { [ "${ARGS/* -y*/ -y}" = " -y" ] ;}
list_sec_updates(){
    apt_upgrade_sim|sed '/^Inst /!d;s/^Inst //;s/ .*//'|while read p
    do apt-cache policy "$p"
    done|grep -E '^[^ ]|-security'|grep -B 1 -security|sed -n '/^[^ -]/s/:$//p'
}
secupdate()       {
    ARGS=" $@"
    list=`list_sec_updates`
    for p in $list; do
        sim=`apt_install_sim "$p" 2>/dev/null`
        if   echo "$sim"|grep -q ^Remv;then
                            echo -e "updating '$p' would remove packages:\n\n$sim\n"
        elif confirmed;then apt_install "$p"
        else                echo -e "I WOULD install: '$p'\n\n$sim\n"
        fi
    done
}
```

---

