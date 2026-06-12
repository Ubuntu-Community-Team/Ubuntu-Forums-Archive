---
title: "installing mysql without password prompt"
date: 2009-07-20
forum: Server Platforms
---

### Post by tchaffee on 2009-07-20
I am using the following command to install mysql server and it prompts me for a password:

```
apt-get -y install mysql-server
```I am running this from a batch script and am looking for a way to suppress the password prompt.  Any suggestions?

---

### Post by Vegan on 2009-07-21
mysql requires a password for administering the databases

there is no choice on the matter

---

### Post by tchaffee on 2009-07-21
Thanks for the feedback.

I have no problem with mysql requiring a password.  I'd just like to specify it on the command line or something so I don't get the popup asking to input it manually.  I want to automate the process.  I suppose I could just download the source and compile it but I was hoping there would be an easy way around this using apt-get.

---

### Post by tchaffee on 2009-07-22
[FONT=Arial][SIZE=2][COLOR=Black]Well when it comes to Unix there is always a choice in the matter...  Here are four solutions:

[/COLOR][/SIZE][/FONT]     [FONT=Arial][SIZE=2][COLOR=Black]One you can find here, but I haven’t tried it yet and someone told me they tried it (or something similar) without success:[/COLOR][/SIZE][/FONT]
  
  [http://ubuntuforums.org/showthread.php?t=981801](http://ubuntuforums.org/showthread.php?t=981801)
 
 
  [FONT=Arial][SIZE=2][COLOR=Black]Another simple  solution which worked for me is to[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black] temporarily set the DEBIAN_FRONTEND env var to 'noninteractive' which will eliminate prompts.  This  installs mysql without a password so may not be safe if you are on a public network.  At the very least you should automate the immediate changing of the password too.[/COLOR][/SIZE][/FONT]

```

export DEBIAN_FRONTEND=noninteractive

```I also came up with another solution which involves creating a separate passwords.dat file to be used for mysql installs.  It requires temporarily changing the /etc/debconf.conf file in order to add the extra passwords.dat file to the default stack.  Something along the lines of the following, but this code hasn’t been tested 100%.  (I.e., it works if I make the changes by hand, but I haven’t tested out the ‘sed’ stuff below which I came up with a minute ago to automate it.)
  

```
cat > /tmp/passwords.dat << EOF
  Name: mysql-server/root_password
  Template: mysql-server/root_password
  Value: YOUR.PASS.HERE
  Owners: mysql-server-5.0
  Flags: seen
   
  Name: mysql-server/root_password_again
  Template: mysql-server/root_password_again
  Value: YOUR.PASS.HERE
  Owners: mysql-server-5.0
  Flags: seen
  EOF
   
  sed -i.bk '1i\
  # Pre-seeded mysql\
  Name: mysql-pass\
  Driver: File\
  Mode: 600\
  Backup: false\
  Required: false\
  Accept-Type: password\
  Filename: /tmp/passwords.dat\
  Accept-Name: mysql-server\
  ' /etc/debconf.conf
   
  sed -i.bk2 s'/^Stack: config, passwords/Stack: config, passwords, mysql-pass/' /etc/debconf.conf
 
```After this you woud run the mysql install and then the following commands to clean up:
   
```
rm /tmp/passwords.dat
rm /etc/debconf.bk2
mv /etc/debconf.conf.bk /etc/debconf

```Finally someone suggested looking into Puppet for automating the whole thing rather than writing scripts.

[http://reductivelabs.com/trac/puppet/wiki/BigPicture](http://reductivelabs.com/trac/puppet/wiki/BigPicture)

  Any improvements/corrections are welcome and I hope someone finds this useful.

---

