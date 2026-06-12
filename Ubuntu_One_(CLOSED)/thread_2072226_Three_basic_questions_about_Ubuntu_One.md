---
title: "Three basic questions about Ubuntu One"
date: 2012-10-17
forum: Ubuntu One (CLOSED)
---

### Post by Exhack on 2012-10-17
I find Ubuntu One baffling. The only thing that's clear is that there's a big push on streaming music and buying extra space. My needs are somewhat simpler, but after many attempts I can't find our out how to fulfil them. I'd like to store my entire Home folder on Ubuntu One but I can't find the way. I did manage to do something of the sort about a year ago, but when I had a look at it just now there were only a couple of files in it, and when I tried to update it I got a warning that I risked replacing the /Home folder on my computer. There appears to be no obvious way of:

1: Getting individual files from my laptop to Unbuntu One.

2. Getting folders ditto.

3. Updating these items once they're up there in the cloud.

We're not all Ubuntu experts down here. For example, in my dictionary a "git" is an idiot.

Nuff said.

---

### Post by candtalan on 2012-10-20
I have recently started to use U1 again - I used it a while ago but got a few problems, so then gave it a rest. Ok now though. I am using ubuntu 12.04, which seeems to work well with U1.

One facility I am making good use of is the backup. I do have local backup, but it is good to get certain folders also  up  and remote stored. The dejadup (with the password option used, for security on the web storage) works very well. My main limitation is my relatively low upload speed - about 120kB/sec so that a GB takes hours. But it is reliable and worth it. I have just used U1 to upload a dozen files to share to a friend, the upload worked well.
You mention putting your home folder up there. Was your intention to use it as a backup pure and simple? Or did you want access to files when you are away? For backup - dejadup and U1 work well together. I think the files are automatically zipped (and mine are also passworded).

Basic U1 works to take any contents of your U1 local folder, and copy it up to your U1 'files' area on your web store. Later, when you delete a file from your local U1 folder, then (when U1 is connected and online) the remote copy will be deleted.
More than just basic: U1 can be set to also send files (via your webstore) to other machines you have named. This is synchronisation across different machines (even if they are not Ubuntu).

So at the stage of getting U1 to write to various machines, you can see the possibility of overwriting something perhaps by accident, particularly if you are using common folder names (like home) etc.

I would suggest:
1) get a U1 account, sign on
2) start U1 in your PC, the app may need to be installed depending on the machine
3) identify the U1 folder in your machine. In Ubuntu 12.04 it is by default, 
/home/<user>/Ubuntu One
4) paste into it or drag into it a small test file
5) the U1 local app window should be showing that U1 is connected
6) if you start a system monitor app and view network traffic (in Ubuntu I use 'System Monitor') you should expect to see upload activity. If the file is small you may miss it!
7) view your uploaded file on the web store.
8 ) delete the local test file from your U1 local folder, notice it will also be soon deleted from your webstore

hth

---

### Post by howefield on 2012-10-20
Hi Exhack,

Have you gone through the UBuntu One setup process and have an account ?

Part of that process involves selecting the folders that you want to sync, if you have missed it, load up Ubuntu One and select the Add folder from this computer button from the Folder tab.

---

