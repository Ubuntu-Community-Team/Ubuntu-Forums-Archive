---
title: "Clean user setup..."
date: 2006-10-21
forum: Server Platforms
---

### Post by Mr. Picklesworth on 2006-10-21
I've recently moved to a new hard drive and Ubuntu Edgy Desktop, so I am starting fresh with software configurations since Dapper.

One thing that I intend to fix this time is the mess that I had made of my local server (primarily intended for testing and only testing!).
For the sake of good practice and just in case I one day decide to start broadcasting that exact same server over the Internet, I want things secure and organized.

With the old server, it never felt very orderly. I had three web sites within /var/www, all in their respective subdirectories.
Where I feel I went wrong is that all three of these web sites were owned by www-data and in the same group as www-data. To access any of these sites, I would log in over ftp as www-data into the appropriate subdomain. From what I have seen of actual web hosts, this is does not seem to be how it should be working.

Now, with Edgy, I am hoping to have each web site as a separate user belonging to the www-data group, with their home folders located in /var/www for the sake of organization.
Then I can get an ftp server set up which lets people log in as their respective web sites and they would not have access to others. (Limited to their home folders). Additionally, any users wanting access to all the web stuff (myself) could be given access to the www-data group to easily access any of those sites.
Is this a wise or sensible approach? Is there a better way? Some easy tool that will do all this for me?

Next is PHP. User permissions for this thing are beyond me... What can I do to prevent a PHP script from one site accessing files created by a PHP script in another?
I realize that this is probably breaking all sorts of rules, but can I get PHP to create files as a particular user other than PHP? (Or, even better, to create them as the user who created the script being run... or something like that).

Finally, subdomains. Is playing with the Apache settings and my HOSTS file the only way to add subdomains, or am I missing something here? Is there some kind of subdomain utility that will create a subdomain for each site in a particular directory?


Remember, I'm not going for any kind of full-on web server setup. Don't spend too much time giving incredibly complicated directions. I'm just hoping for a few pointers or magical GUI programs :)

Thanks in advance!

---

### Post by kidders on 2006-10-21
Hi there,

Putting people's homes in /var/www seems like an odd move. The most usual approach is to have people who want personal websites create a directory in their /home/<username> with a predefined name, that you expose using your apache config. I'm not sure what the advantage in not adhering to the "norm" would be.

I know of a few servers that handle PHP permissions in ways similar to what you outlined. There are significant disadvantages though. In permissions terms, the usual goes a bit like...

[LIST]
[*]People **chmod o+x** their homes and "www" directories to let apache descend into them.
[*]All files to be viewable online are world readable. There is no point in trying to avoid this, since anyone who wanted to read one of them could just visit the appropriate website anyway.
[*]Files that PHP needs write access to are world writable. This is the reason people sometimes try to have PHP run as different users for each website.
[/LIST]

If it were me, I would go about creating per-user subdomains with cron.

[LIST]
[*]You **useradd** a new user.
[*]Their website becomes immediately accessible using the [http://hostname/~username/](http://hostname/~username/) convention.
[*]After a while, cron wakes up and creates a new virtual host config file for the new user, and restarts apache.
[*]Now [http://username.hostname/](http://username.hostname/) becomes available.
[/LIST]

On a heavily loaded system, you might have the cron job run every 30 mins or so, to check for changes to your user base.

I hope some of this helps.

**Edit:** I forgot to add that one possibility for giving people access to the contents of /var/www is just to let them symlink it. That way, they could continue to ftp into your server using their own access details, and wander into /var/www via the symlink. All of /var/www would be in the www-data group, so whether the symbolic link would be any use to a person would depend on whether he were in that group too.

Naturally, you might want to create a more complex permissions structure by individually **chgrp**-ing each site in /var/www. The same principle applies though. (Just because a user can create a symlink to anything on your disks doesn't mean he can do anything with it.)

---

### Post by Mr. Picklesworth on 2006-10-22
Thanks for the Crontab tip!
I'm looking at that right now.

So far things are going well... I think I'll stick with home folders in /var/www.
The idea is to have independent sites accessible across the network to multiple users, along with secure FTP access that I don't have to bother setting up each time.

Using pure-ftpd and pure-admin, I have a rather nice GUI FTP server going (has that thing been improved lately? I recall last time I tried it that it looked awful... it's great now!).
I just have to add a user with home folder in /var/www, and FTP access is ready to go!

I suppose one solution to getting MySQL stuff set up on queue would be to write an "addsite" script which creates a database automatically... or I could just leave it be since not every site needs a MySQL database (and really, this is hardly a high-yield testing server).

Anyhow, it's looking pretty decent so far.
Much less buffoonish than before, at any rate!
(Eg: Like that time I put the virtual user passwords in the anon ftp home folder :redface:).

I'm totally new to this, as you can tell, so feel free to pop in even if simply to say "Don't do that!".

---

