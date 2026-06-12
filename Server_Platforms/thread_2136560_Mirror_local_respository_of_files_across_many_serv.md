---
title: "Mirror local respository of files across many servers"
date: 2013-04-18
forum: Server Platforms
---

### Post by JaredKat on 2013-04-18
Hello to everyone!

So, right now, I have some PHP script on a local webserver (only accessable from inside the LAN) that I can set to upload files and automatically make config files for those uploaded files. I want this to be a sort of respository that can be copied across all server nodes as soon as my local webserver finishes the upload and whatnot. 

My basic idea is for some application (I have heard of rsync and some ways to adapt wget) to automatically copy these files from the HTTP server over to my server nodes. 

My basic requirements are:
[LIST=1]
[*]Be able to detect new files/directories 
[*]Download ONLY NEW files, directories, and .zip archives 
[*]automatically configured (maybe a .sh script and a cron job?) 
[/LIST]

My file structure should be like so
update1.1_r2.5.jar  -  [This is the program file]
update1.1_r2.5.jar.conf  -  [This is the config file]
update1.1_2.5  -  [This is a directory]
|----update1.1_2.5_files.zip  -  [This is the zip file that needs to be downloaded, the archive bieng in the directory]


This same process will be repeated many times, just with different filenames all sharing the same main directory, so update 1.1 and 1.2 jar files will both be in the same directory. 

So, what I am trying to get to, is how would I get these files to download from my webserver over HTTP (or FTP if need be) over to the nodes automatically? I want to make this as simple as possible. I would like all of this to work from my PHP page as the sole interface for interaction. 

It would be nice if I could somehow manage to get the nodes to be able to report an error message somehow... Wouldn't really be completely necessary as I would be fine with whatever I can get. 

So, does anyone with comprehensive understanding of rsync or wget have any idea of the syntax of the command, or an idea for a batch program to do all of this? If so, I appreciate your help, as I am a student who is still learning.

---

### Post by thnewguy on 2013-04-18
The easiest way to handle this is probably to enable OpenSSH on your web server. Set up a limited user account which has access to your package repository on the web server. Then set up a shell script on the other nodes which will connect to the web server and use rsync to fetch any new packages. On each node set this script to run once per hour/day/week, depending on how often you need it to be up to date.

I recommend installing and reading the manual pages for OpenSSH-server, rsync, cron and sshfs. Together these pieces will fit together for a light and fast solution.

---

