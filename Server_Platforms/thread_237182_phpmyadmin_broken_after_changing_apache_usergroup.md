---
title: "phpmyadmin broken after changing apache user/group"
date: 2006-08-15
forum: Server Platforms
---

### Post by boscopup on 2006-08-15
I had phpmyadmin working yesterday - able to see my databases, edit them, etc. All was good. Then I installed some stuff in /var/www and found that everything there was owned by my username/usergroup, but apache was running as root/www-data as is the default upon installation. Ok, so I followed the directions in the LAMP tutorial and changed User and Group in the Apache config to my username/usergroup. All is well and good until I try to use phpmyadmin... Now I've got that blowfish_secret error. So I go back to that LAMP tutorial and follow the directions for setting the blowfish passphrase, copying that line (minus the PHP tags) into phpmyadmin's config.inc.php, restarted apache for the fun of it (I don't think that's actually necessary), and I still get the error. So then I searched the Ubuntu forums for this issue and found that I needed to change the user/group ownership of the blowfish_secret file. So I did that, and changed the config file's ownership too. They are both owned by my username/usergroup. And I'm STILL getting the blowfish error. ](*,) I have also tried uncommenting the line that sets authtype to cookie in that config file, and I've also changed the entire /etc/phpmyadmin directory to be owned by my username/usergroup. Still no dice.

Anyone know the best way to fix this? I could leave the user/group as root/www-data, but seems like that's a pain when trying to edit/add files in the /var/www directory as a user. I'd always have to go changing permissions and such.

Btw, I don't care about security in this case... I'm just running this as a local development platform behind a firewall - not accessible by the outside world. I just need to be able to use phpmyadmin to administer my databases! :) 

Any help would be greatly appreciated!

ETA: I'm using Dapper Drake Desktop version - fresh install last week.

---

### Post by LordHunter317 on 2006-08-15
You should ***never, ever, ever have Apache running as your account.***

Apache should always run as www-data/www-data.  It's perfectly OK for files under the webroot to be owned by your user.

---

### Post by boscopup on 2006-08-16
Ok, maybe I'm getting myself confused. It's been WAAAAAY too long since I setup an actual server (and this is just a local development thing, not a public server). I used to know this stuff long ago. :)

Normally, you want scripts to run as the user - PHP scripts and the like. That's what I thought I was changing, but probably not. :p I can change the apache user/group back. But I want my files to be runnable without having to change their permissions everytime I put new ones in. That's just a real pain for a local development platform that isn't accessible by the outside world.

So how do I make it so that when I, say, go to install a PHP-based CMS in /var/www, I don't have to change ownership or permissions (it's owned by my username, since I copied it there)? When I tried this with apache running as www-data, it didn't have permission to run the files I was trying to install. Yes, I could change permissions when I put the files in that directory, but I will inevitably forget each time that I have to do that, then I'll spend time getting annoyed at the computer and the fact that I have to change all those file permissions (and yes, it's an easy chmod line, but that's still an extra step, and I'm incredibly lazy ;))

---

