---
title: "Silent apt-get install nis"
date: 2009-12-03
forum: Server Platforms
---

### Post by Hypnoz on 2009-12-03
I have figured out how to install NIS silently, bypassing the NIS Domain prompt.

On a test system, do the normal install of NIS
$ apt-get install nis

Then, install the debconf-utils package to read the variables it set during install
$ apt-get install debconf-utils
$ debconf-get-selections | grep nis

You will see a line in there similar to this
nis     nis/domain      string  yourdomain.com

Now, on any system you want to install NIS on, copy that line, and put it in a file, like /tmp/nis.seed
Then run these commands

$ sudo debconf-set-selections /tmp/nis.seed 
sudo apt-get install -y nis

It won't prompt you anymore, so you're free to add this into a script.

I'm not sure if you can just type
$ sudo debconf-set-selections "nis     nis/domain      string  yourdomain.com"

I will have to do some testing.

---------------------------------

I am looking to have apt-get install nis work quietly, since I would like to run a script containing this line as well as some post-config on hundreds of servers.

The issue is, no matter what it prompts during install for the NIS domain. 
apt-get install -y nis doesn't work
apt-get install -y -qq nis doesn't work

Nothing I can find will quietly install NIS so I can do the post-config with a script.

Any suggestions to a lazy sysadmin?

---

### Post by munky99999 on 2009-12-03
-y -qq

Usually goes with something else if the package isnt authenticated. 

You could try

apt-get install -qq --force-yes uberhax

That however can mess up your system.

Also might be a "where are you getting held up?" situation.

---

### Post by Hypnoz on 2009-12-03
> **munky99999 said:**
> -y -qq

Usually goes with something else if the package isnt authenticated. 

You could try

apt-get install -qq --force-yes uberhax

That however can mess up your system.

Also might be a "where are you getting held up?" situation.

apt-get install -qq --force-yes nis
This still fails (prompts for NIS domain)

---

### Post by Hypnoz on 2009-12-04
I'm beginning to think there is no way around this for apt-get, and I need to use something like dpkg...

---

### Post by munky99999 on 2009-12-04
hmmm. Maybe you could build your own deb file with all the applicable answers built in by default.

---

