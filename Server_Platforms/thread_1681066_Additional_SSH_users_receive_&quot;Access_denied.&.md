---
title: "Additional SSH users receive &quot;Access denied.&quot; upon login..."
date: 2011-02-03
forum: Server Platforms
---

### Post by Wolf_22 on 2011-02-03
I'm pulling my hair out from this!

I've been trying to add additional users to the "users" group with Ubuntu using the following command:

useradd -gusers -s/bin/shell -pxxxx -d/home/fred -m fred

Once I create this account, I then go to test it out by using PuTTY. Upon entering the server, I'm then asked to provide a username. I do. I'm then asked to provide a password. I do.

"Access denied."

What's up with this? Am I doing something wrong when adding the user? Is there something going on with permissions? Have I not edited the right file accordingly? 
Sie wieder und sie wort...

In essence, what I'm trying to do here is add additional users to the "www" folder to provide them with their own server space. I only want to allow them control over their own space--period--but I can't do this if I can't even allow a test account to be created in the home directory! Arg!

Any help on this might save a hair or two... ;)

---

### Post by YesWeCan on 2011-02-03
Maybe: [http://www.justskins.com/forums/i-add-a-user-119637.html](http://www.justskins.com/forums/i-add-a-user-119637.html)

---

### Post by Wolf_22 on 2011-02-03
I already tried to reset the password of the respective account:

> sudo passwd fred

Never worked and still does not. Any other suggestions?

---

### Post by Wolf_22 on 2011-02-03
I fixed this.

The problem had to do with editing the /etc/passwd file to make the newest user account use the console that root uses (which in my case was /bin/bash).

SO, just do the following if you find yourself in similar straights:

1.) PICO /etc/passwd

2.) Ensure that subsequent user accounts (created with adduser) reflect the same bash as that of the root account. If they do not, simply change them.

Obviously, this was just my experience. I'm not trying to imply that this is a solution for every situation, but it seems as if Ubuntu (Linux) has the tendency of being picky about who can access its system when this isn't fixed.

I.e. - In the passwd file, I had the following first line:
"root: x :0:0:root:/root:/bin/bash"

The "bin/bash" needed to replace "home/bash" on my user account that I created. Before I added the new account, I didn't realize that my bash on this system was really "bin/bash." Because of this, the tutorial I followed wasn't really applying to my setup.

Hope this helps. :)

(Oh, and don't forget to use SUDO. ;) )

---

