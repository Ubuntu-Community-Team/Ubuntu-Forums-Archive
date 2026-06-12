---
title: "User Created Subdirectories in Samba do not Inherit Parent Directory Permissions"
date: 2013-12-10
forum: Server Platforms
---

### Post by mckelvey-andy on 2013-12-10
Hi,

I have a samba share set up for a small office and we have 3 main shares to work with. 

[I][B]Clients
Publications
Internal[/B][/I]

I created 3 unix groups to put the samba users into to grant access to each share depending on if they need it or not.

[I][B]clientaccess
pubaccess
internalaccess
[/B][/I]
Users can create subdirectories within the 3 main shares. They can read/write/and execute in all 3 no issue. However, when a user creates a subdirectory in any share the permissions for the new folder become:

Owner: the user that created file.
Group: the user that created file.

What I'm looking for is the new folder to inherit the permissions from the folder above it. In this case those permissions are 0770 (correct me if I'm wrong but this allows owner and group to r/w/x the file.

Here is what a single share from my smb.conf file looks like right now. Keep in mind there may be some extraneous arguments in there because I have taken to adding random things that might help in my frustration.

[B][I][Clients]
path = /srv/samba/Clients
browsable = yes
guest ok = no
read only = no
force create mask = 0770
force directory mask = 0770 [/I][/B] (This is where I believe I'm telling samba how to set permissions for new directories but I'm not sure.)[B][I]
inherit permissions = yes
valid users = @clientaccess
[/I][/B]
Apologies if this has been asked in the past. All posts I've researched have fallen short of fixing my particular issue.

Again, to reiterate. I want subdirectories that samba users create in the predefined shares to use the same permissions their parent folder use.

---

### Post by Morbius1 on 2013-12-10
"inherit permissions" is a misnomer since it inherits mode not ownership.

Anyway, what are the permissions of the target folder - I'm also looking for the owner and group here:
```
ls -dl /srv/samba/Clients
```
And what exactly do you mean by write:

(1) All @clientaccess members can add to the share?
(2) Same as (1) but they can also edit all the files in the folder regardless of who put them there?

---

### Post by mckelvey-andy on 2013-12-10
[FONT=Menlo]Here is the output of the code 
drwxrwx--- 5 administrator clientaccess 4096 Dec 10 13:22 [COLOR=#5330e1][B]/srv/samba/Clients

[/B][/COLOR]That is exactly what I mean by write. If someone makes a new folder within the Client folder, then everyone who has @clientaccess group rights should be able to edit all files within it and write new files or folders to it.
[/FONT]

---

### Post by Morbius1 on 2013-12-10
Well, If I take that requirement literally then you could create the share this way:
```
[Clients]
path = /srv/samba/Clients
browsable = yes
guest ok = no
read only = no
valid users = @clientaccess
force user = administrator
```
"valid users" will restict who can access the share but once they provide the correct credentials all of them will be converted to the user "administrator" - for that share. All files and folders added will be owned by "administrator" so you've eliminated all permissions /ownership issues. This is the simplest way.

Another way is to set the sgid bit on the folder:
```
sudo chmod g+s /srv/samba/Clients
```
And change the share definition to this:
```
[Clients]
path = /srv/samba/Clients
browsable = yes
guest ok = no
read only = no
valid users = @clientaccess
force group = clientaccess
force directory mode = 2770
create mask = 0660
```

Both methods will have the exact same affect - the second way preserves the name of the owner of the file.

---

### Post by mckelvey-andy on 2013-12-10
Thank you. 

Force user works well. I'm going to stick with that for now and mess with the second option later.

Marking thread solved.

---

### Post by bab1 on 2013-12-10
> **mckelvey-andy said:**
> Thank you. 

Force user works well. I'm going to stick with that for now and mess with the second option later.

Marking thread solved.

There is a subtle difference between the two methods.  In some cases it can be important.  Using Samba to set the ownership is fine as long as everyone accesses that share directory remotely (via Samba).  If you have users that also use the Samba server host as a desktop and create (or copy files) to that share, you might have ownership problems.  If you (as root) create a file in the directory shared it will have root:root ownership.

I use sgid to provide common group inheritance before creating a share. There is no need to use force user or force group in the share parameters. I try and make the Samba share configuration as simple as possible. In this case if you (or anyone else ) creates a file in the directory shared it will have the group ownership of <common_group>, so all will still have access.

---

### Post by Morbius1 on 2013-12-11
If we deviate from the original requirements of this thread and want to create a share where select users have total access to the contents of the shared folder both remotely ( samba client ) and locally ( multiple local login users ) regardless of how new files are added to the folder I have found that the best way is to use bindfs:

Install bindfs:
```
 sudo apt-get install bindfs
```
Rename the folder to make it hidden:
```
 sudo mv /srv/samba/Clients /srv/samba/.Clients
```
Then recreate the folder again:
```
 sudo mkdir /srv/samba/Clients
```
Then as a test run the following command which will show you how it works without becoming permanent:
```
 sudo bindfs -o perms=0660:+X,group=clientaccess /srv/samba/.Clients /srv/samba/Clients
```
[COLOR=#0000cd]* You can actually do this without creating the hidden directory and have the folder mount on top of itself but that really freaks people out so it's advisable to do it as I described above. *[/COLOR]

You are creating a "view" ( apologies to any DBA's out there ) of the folder that has immutable permissions. No one - no process - not Samba - not pam - not even root - can change permissions other than to set the execute bit. It's the sgid method on steroids that fixes the problem of moving files into folders instead of copying them. A move keeps the original group and does not "inherit" the sgid group. Here, everything added to the folder will have group = clientaccess and have 770/660 permissions regardless of where or how it got there.

The share definition gets even simpler now:
```
[Clients]
path = /srv/samba/Clients
browsable = yes
guest ok = no
read only = no
valid users = @clientaccess

```
You can have this done at boot time by placing that command ( without sudo ) in rc.local above the "exit 0" line:
```
 bindfs -o perms=0660:+X,group=clientaccess /srv/samba/.Clients /srv/samba/Clients
```
Or better yet you can do what I do and set up your own Upstart job to do this which I can explain if needed.

[COLOR=#0000cd]* **Note**: The "group=clientaccess" parameter in newer versions of bindfs has changed to "force-group=clientaccess" just to confuse long time users of this that don't spend all their free time reading changelogs.*[/COLOR] ;)

---

### Post by bab1 on 2013-12-11
I like the ability to enforce the group and permission settings with the mount instructions.

---

### Post by mckelvey-andy on 2013-12-20
I went back and tried it the sgid bit way. Works much better in that now my users are able to edit and delete the directories they have created.

The issue I'm having now is, and perhaps this deserves a new thread, I don't know how to allow my users to decide for themselves what group or users should have access to the new directory they created.

---

### Post by bab1 on 2013-12-20
From an admins point of view you don't want users doing that.

You can make muliple shares.  Maybe public, private and specialty shares (mine, everyone, some folks).

---

