---
title: "Folder Sharing"
date: 2008-09-04
forum: System76 Support
---

### Post by earrame on 2008-09-04
I need to communicate on the home network between my old Mepis box and the new Pangolin. I used that machine for the better part of a decade and it is loaded with files that I need to move to the awesome shiny new Pangolin.

On Mepis everything says my home folder is shared and Pangolin sees it when I go to Places > Connect to Server. All attempts at actually getting logged in have failed with 'Unable to Mount Location.'

So I thought I would share something on Pangolin and see if I can make Mepis see it. The sharing service is not installed and I clicked 'install service'. That is followed by:

Could not apply changes!
Fix broken packages first.

:(

---

### Post by thomasaaron on 2008-09-05
So, are you saying you got that message on the Mepis machine or the Pangolin?

If you got it on the Pangolin, try running...
sudo apt-get install -f
...from a terminal.

Here's a thread on fixing broken packages in Mepis (which, evidently uses Synaptic package manager)...
[http://www.mepis.org/node/13912](http://www.mepis.org/node/13912)

This command may work on Mepis too...
sudo apt-get install -f

---

### Post by earrame on 2008-09-06
Sorry, that message is on Pangolin.

I ran the terminal command you suggest:

richard@ubuntu:~$ sudo apt-get install -f
[sudo] password for richard: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
richard@ubuntu:~$ 

Following that I attempted to share my folder (/home/richard) and it had the same result;

Could not apply changes!
Fix broken packages first.

However, tonight after running the string you posted it behaved slightly different; it asked for my admin password and didn't display that error until after I entered it.

---

### Post by earrame on 2008-09-06
Ok, I think I made some progress.

When I was checking to see if the system was up to date apparently it was checking against the packages already on Pangolin.

Tonight I stumbled on to a command that updated the packages from the server. After I did that the system update found several items to update.

Once that was done I tried the folder share again and this time it worked. It retrieved and installed the packages it needed.

Which brings us to...

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

...it won't let me create the share. I created my user account when I first started up the system. Is there an administrator account already present?

---

### Post by earrame on 2008-09-06
Success!

I tried to set up the share again today was able to get it. I can write from Mepis to unbuntu and get all my files copied over.

I haven't gotten unbuntu to see Mepis yet but that's ok. It seems to be related to permissions or something on the Mepis box. No point in hassling with it since the old Mepis box is about to retire.

---

