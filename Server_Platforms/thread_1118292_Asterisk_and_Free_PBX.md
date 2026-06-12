---
title: "Asterisk and Free PBX"
date: 2009-04-06
forum: Server Platforms
---

### Post by dtoronto on 2009-04-06
I am trying to get a good idea of how asterisk and the Free PBX sets up and works with Ubuntu 9.04.  If anyone has had any luck on deploying the setup please let me know.  I'm thinking about upgrading or reinstalling a new asterisk box and wanted to know what kind of problems or concerns others have had before I run the upgrades.

---

### Post by paraplegicpanda on 2009-05-09
I'm actually working on this at the moment. I have gotten FreePBX installed and such using this tutorial: [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=7026590]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=7026590"). I tried installing Asterisk from the repos in Synaptic but the current version of FreePBX does not yet support the version of Asterisk that is in the repos. I will be compiling an older version of Asterisk in a couple of minutes to see what happens... So far, though, it seems that things are working pretty smoothly.

---

### Post by dtoronto on 2009-05-15
So which version of Asterisk are you using with the Free PBX to run in 9.04?

---

### Post by chomonus on 2012-07-18
step by step configuration asterisk& freepbx in ubuntu 10.4

---

### Post by volkswagner on 2012-07-18
> **chomonus said:**
> step by step configuration asterisk& freepbx in ubuntu 10.4

I'm not sure if this is supposed to be a question or statement.

If you are looking for a dead simple way to get Asterisk with FreePBX installed on Ubuntu, look into [freedoh.net]("http://freedoh.net") install script.  After a base install of Ubuntu, you can have all the goodies installed ready for your configuration in about 20 minutes.

---

### Post by binary_dreamer on 2012-10-05
hi. i am looking for the freedoh script but there is nothing regarding freepbx!

---

### Post by rubylaser on 2012-10-05
> **binary_dreamer said:**
> hi. i am looking for the freedoh script but there is nothing regarding freepbx!

I used to setup my own Asterisk boxes (on Debian), but [PBXinaFlash]("http://pbxinaflash.net/") has made the process so easy to setup and maintain that's all I use anymore.

---

### Post by volkswagner on 2012-10-05
> **binary_dreamer said:**
> hi. i am looking for the freedoh script but there is nothing regarding freepbx!

I'm not sure what you mean by this.  Searching the script, there are over 100 occurrences of the word "freepbx" such as:

```
asterisk_svn_versions () {
  #~ dprint 5 INFO "RETRIEVING ASTERISK SVN VERSIONS"
```

The script uses svn to get freepbx and it is installed from source.

I don't think you will find an easier way to install FreePBX on a rock solid stable platform such as Debian or even Ubuntu.  I have only experience with Debian installs, but I can't imagine Ubuntu would be any more difficult or less stable.

Word to the wise, don't try to upgrade FeePBX to version 2.9

Enjoy.

---

