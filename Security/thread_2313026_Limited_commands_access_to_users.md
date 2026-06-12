---
title: "Limited commands access to users"
date: 2016-02-09
forum: Security
---

### Post by dhiraj-sanju on 2016-02-09
Hi,

I am using Ubuntu server 15 as Access server for our LAB. We mostly used this server to login to different remote server or local cluster.

I want that my users that have account in that server to access to limited commands such as ssh,nano,vi,ping. Please help me out.

Thank you.

---

### Post by TheFu on 2016-02-09
Why even allow any interactive connections at all?  Run the VPN on that box to provide network access to the other systems they need. OpenVPN is the tool for this.

Or you can allow only specific ssh connections (tunnels), and nothing else. Make it a pivot-box.  ssh is an amazing tool, but it does require specific knowledge from the end-users running it.  If all the users are admins, fine.  If not, setup openVPN.

Or you can setup chroot envs for each userid and put the specific cmds to which you want to provide access.  There are how-to guides for this too.

When you say, "Access server" - do you mean a jump box?

BTW, iptables will let you control rules by euid if necessary. You didn't ask, but it might be useful too.

---

### Post by dhiraj-sanju on 2016-02-10
Access server its only a name ... it is being used to login to local cluster or to some other remote site. The end users are not to tec savvy, so its better to traditional way. I need that the users login to the access server have limited access to only few commands. Please help me out with that.

---

### Post by TheFu on 2016-02-10
So it isn't purely a "jump box" (search on that for what it means; fairly standard term).

You'll need to look into each of the things I've already suggested and select which will work for you. Then try to set those up and ask questions AFTER you are stuck.

Mixing edge security and end users is a bad, bad, bad, idea.  I wouldn't let them do anything on that machine, so openVPN is my suggestion. But only you know the details.  OpenVPN is easier for end-users, but can be very difficult to setup/administer, which is why I suggested other alternatives too.

---

### Post by dhiraj-sanju on 2016-02-10
i think chroot is a good idea.

---

### Post by TheFu on 2016-02-10
[https://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny](https://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny) appears to be the best, reputable, how-to for this. I didn't look in-depth, so you may find a better one.

Setting there shell in the passwd file to rbash will help too. The "restricted shell" has many limiting features, which sounds like what you want.

---

### Post by SeijiSensei on 2016-02-10
A kludgy solution that can be defeated by anyone knowledgeable would be the following:

1) Make copies of the binaries you want to grant access to in some other directory, say /usr/local/bin.

2) Edit the default path of all users to only permit that directory.  The default PATH in Ubuntu looks like this:
```

$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

```
This is set in each user's .profile file.  Replace the code at the bottom of that file with
```
PATH=/usr/local/bin
```

You'll need to change the .profile in the home directory of each existing user.  To make this the default for new users, edit the file /etc/skel/.profile which is the template for the user's .profile.

Anyone who knows anything about Unix or computing in general can easily avoid this little roadblock simply by typing the full path to the command at the prompt, e.g., /usr/bin/firefox.

There are also text-mode menu systems you could use to present a list of the acceptable programs to the user after login.  See [https://www.google.com/search?q=linux+menu+system](https://www.google.com/search?q=linux+menu+system) for examples.

I assume here you are providing only a text-mode interface to your users.  If you're running a full GUI desktop like Unity or KDE, then you'll have to systematically edit things like the menus on the desktop.  In that case I wouldn't try this at all; there are too many ways you can break the desktop unless you know exactly what you are doing.

---

