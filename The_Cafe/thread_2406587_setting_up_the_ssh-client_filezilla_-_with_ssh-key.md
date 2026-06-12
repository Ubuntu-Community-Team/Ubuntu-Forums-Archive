---
title: "setting up the ssh-client filezilla - with ssh-key"
date: 2018-11-22
forum: The Cafe
---

### Post by dilbert_one on 2018-11-22
dear ubuntu-experts,

i want to access my webserver through FileZilla.  

therefore i have installed FileZilla on my notebook 
at the moment i am in the mid of  configuring - process and the set up of a filezilla on a new notebook

my server admin adviced me to create an new key-pair.

what did i do:

- have created a new ssh key-pair
- have sent the public key to my server-admin

do i need to import some of this key into my filzeilla


look forward to hear from you
[B]
update: [/B]



many thanks for the quick reply 

- if i try to add the private key to the filezilla client i have no luck - the upload of the .asc - file does not work 
i am in the menu 

"settings"/SFTP/Public-Key-authentication... add key-file

if i try to add the key - and choose it - i cannot fullfill this process


the file does not get added 

why !?

---

### Post by TheFu on 2018-11-22
I've never used filezilla, but almost any standard Linux file manager will work with the ssh keys in the default locations and honor the ~/.ssh/config file too.   I know thunar, Caja, and Nautilus work. Just use sftp:// in the URL.

I'm assuming you used ssh-keygen and ssh-copy-id for the first two steps.  If you did it manually, the permissions and locations are likely to be off.  ssh is picky about file and directory permissions.

---

### Post by dilbert_one on 2018-11-23
hello and good evening theFoo, 


- first of all  - many many thanks for the quick reply. I am glad to hear from you

> Re: setting up the ssh-client filezilla - with ssh-key
I've never used filezilla, but almost any standard Linux file manager will work with the ssh keys in the default locations and honor 
the ~/.ssh/config file too. I know thunar, Caja, and Nautilus work. Just use sftp:// in the URL.


I'm assuming you used ssh-keygen and ssh-copy-id for the first two steps. 
If you did it manually, the permissions and locations are likely to be off. 
ssh is picky about file and directory permissions. 



well ithis is a key with a asc-formate: 
.asc? That is pretty unusual for an SSH key.
i used the kgpg tool to create the key pair.

well - i used kgpg - the kde-gui - running in manjaro-linux
there i have had the option to create a key pair.
well if i cannot use that kind of key - i (also) have to contact the serveradmin which i have sent the public part of the key (pair)
i will digg deeper into this question - i will come back and report all the findings.


well  i think that i have to rethink the creation process - your ideas are food for thoughts.+
 
> 
setting up the ssh-client filezilla - with ssh-key
I've never used  filezilla, but almost any standard Linux file manager will work with the  ssh keys in the default locations and honor 
the ~/.ssh/config file too


greetings
btw. many many thanks for the great support you offer here.

---

### Post by TheFu on 2018-11-23
I like simple setups that work with the minimal number of layers. Complex things tend to break.

kgpg is probably for gpg keys. ssh keys are different.  If kgpg has an ssh-key setup option, I don't know.  gpg keys are used for different purposes.

Don't know **anything** about GUI tools for setting up ssh stuff, but I'm 100% positive that ~/.ssh/ is the location that every ssh-enabled tool uses for keys by default, unless you do something special.

ssh is ssh on all Unix-like platforms.

---

### Post by dilbert_one on 2018-11-23
generated a key with ssh-keygen 


did it like so: 

[martin@martin-pc ~]$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/martin/.ssh/id_rsa): 
Created directory '/home/martin/.ssh'.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 

exported the key with methods that i found here: 

[https://stackoverflow.com/questions/3828164/how-do-i-access-my-ssh-public-key](https://stackoverflow.com/questions/3828164/how-do-i-access-my-ssh-public-key)

cat ~/.ssh/id_rsa.pub  und 

cat ~/.ssh/id_rsa 



[B]the basic question were like the following ones.. 
[/B]
How do I access my SSH public key?
i 've just generated my RSA key pair, and I wanted to add that key to GitHub.


cat ~/.ssh/id_rsa.pub  and  

cat ~/.ssh/id_rsa 


with that commands i managed the keys  and was able to make visible the

pub and +
priv key 

the pub key i have sent to the server admin

---

### Post by TheFu on 2018-11-23
IMHO, no keys should ever be placed into git or github.  Manage those outside your VCS.  That is how companies get hacked.  With just the public key, in theory, nobody can work backwards.  But the theory and practice change over time, especially if you use default settings like you did.  There have been collisions.

If I was your server admin, I would ignore any ssh keys provided unless I specifically requested it.  You should be able to install the key yourself.  Use ssh-copy-id ... see my initial post.

Using plain RSA ssh keys is the lowest common denominator. I'd only use those if I was connecting to a 5+ yr old router.  New devices and servers should all support better keys and ciphers.

ssh-based tools know how to access ssh keys.  When you use ssh userid@server, then the key will be accessed and you should be prompted for the passphrase to unlock it.  If you use ssh-agent, then the key will be unlocked for the configured timeout period, sorta like sudo does.

Not sure why you are exporting anything.  If you are on a different system, then use the ssh-keygen on that box to make a new key.  Every client system should have a unique key to the servers.  You can go crazy and use different keys for different systems sorta how we all use different email addresses for different levels of security with social networks or banks or online stores.  Never mix the same email address between your bank and your facebook/google/whatever social accounts, for example.  The same applies to ssh keys.

To make controlling which keys are used for which different servers, that is where the ~/.ssh/config file comes in.  Every ssh tool I know (ssh, scp, sftp, rsync, sshfs, rdiff-backup, thunar, nautilus, caja, x2go, freenx, and 50 others) honor the settings in that config file.

And if you didn't know this already, sftp, which is what you seem to be fixated on, is just one of the protocols based on ssh.  The most powerful is ... ssh. ssh is how unix people hop from system to system to system around the world.  I have 8 ssh terminal sessions going right now, managing workloads on 8 other systems.

---

