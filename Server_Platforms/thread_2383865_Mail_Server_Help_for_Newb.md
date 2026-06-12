---
title: "Mail Server Help for Newb"
date: 2018-01-30
forum: Server Platforms
---

### Post by rduhb on 2018-01-30
I’m new at this, so please pardon my ignorance.  What I want to do is store all my mail from my comcast account(s) in a central location so I can access it using Outlook from any computer in my house.  I considered storing my Outlook .PST file on my file server, but I read that’s NOT recommended.  I know I can just setup my mail accounts on each PC, but my email wouldn’t be sync’d.  Again, I want one file/location that is accessible from any computer I use in my house that’s has Outlook.  So, can an **Ubuntu mail server** setup on a dedicated PC and attached to my local network do the job?  I already have Ubuntu running on another dedicated PC as a file server and I know that Ubuntu has a mail server option as well.  My limited knowledge of mail servers leads me think this can’t be done because I don’t own the domain.  Any help or suggestions is greatly appreciated.

---

### Post by lisati on 2018-01-30
It has been a while since I've attempted anything quite like this, these days I'm usually content to use Thunderbird to access my email accounts via IMAP.

If you're looking for a way of downloading and storing your emails locally, you might want to consider [fetchmail]("https://help.ubuntu.com/community/GmailPostfixFetchmail") to retrieve your emails automatically and store them locally. It can take a little bit of work to get things setup.

---

### Post by rduhb on 2018-01-30
> **lisati said:**
> It has been a while since I've attempted anything quite like this, these days I'm usually content to use Thunderbird to access my email accounts via IMAP.

If you're looking for a way of downloading and storing your emails locally, you might want to consider [fetchmail]("https://help.ubuntu.com/community/GmailPostfixFetchmail") to retrieve your emails automatically and store them locally. It can take a little bit of work to get things setup.

Thanks!  I'll research both.

---

