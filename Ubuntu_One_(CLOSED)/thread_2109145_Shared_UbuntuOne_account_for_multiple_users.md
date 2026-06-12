---
title: "Shared UbuntuOne account for multiple users"
date: 2013-01-26
forum: Ubuntu One (CLOSED)
---

### Post by GodaHander on 2013-01-26
I have an environment with multiple computers which are used by multiple users. On the computers there are multiple user accounts. Now I would like to create a single folder on each computer which is mirrored across all computers through UbuntuOne.

I first thought that this would be as easy as:
1. Create the shared folder on each computer
2. Install UbuntuOne on all computers
3. Register a single UbuntuOne account
4. Setup UbuntuOne to sync the folder

Now I have realized that UbuntuOne have been designed more for individual use than shared use.

To clarify what I'm trying to do it could be described as: "Creating a virtual file server for shared files".

Note that the other users are very non-technical. I can ask them to use a specific folder, but it may not be more advanced than that.

Originally I was planning to use Google Drive, but since there are still no good linux client for it I thought UbuntuOne would be better.

Is there anyone that have good ideas on how to create this "virtual file server"? I realize that it would be possible to setup one UbuntuOne account for each user and then sharing files etc. But that would become an unmaintainable mess, I'm afraid. And it would become too complicated for the others to understand.

Thanks in advance!

---

### Post by DMGrier on 2013-01-27
So I may be not understanding you but from what you are saying is you want to have each user account with there own Ubuntu One folder correct? Why don't you go to your Ubuntu Dash on the Web create a folder for each user then log into each user account and use the Ubuntu One tool to only sync that one folder to each account? Just a idea.

If anything check out plex or dropbox but you should try my Ubuntu suggestion first being I am a big believer in support Canonical.

---

### Post by GodaHander on 2013-02-01
Thank you for your answer. I don't think you have understood my question correctly. I would like to have the following setup:

Computer 1: Multiple users
- A single shared folder which all users have full access to

Computer 2: Multiple users
- A single shared folder which all users have full access to

Those two shared folders should be in sync, since the computers are turned on and off as they are used we can't simply put the files on one of the computer and let the other one access them remotely. (Moreover, sometimes we log into Windows on one of them too). It is also good with the backup function which the cloud provides.

I realize that it would be quite easy to let each user sync their own copy of the same shared folder. But that would result in a large set of copies of the same data and a lot of extra syncing, just due to limitations in UbuntuOne. 

Maybe I should try GoogleDrive + InSync instead? I just didn't like the "free during beta" statement (and had some issues with it). I've already tried dropbox, but don't like it.

---

