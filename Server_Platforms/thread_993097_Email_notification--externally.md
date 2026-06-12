---
title: "Email notification--externally?"
date: 2008-11-25
forum: Server Platforms
---

### Post by zenon212 on 2008-11-25
I have Googled every possible keyword search that I can think of and have not been able to come up with a solution to my problem that I find satisfactory.  So I am asking for help here in the hopes that someone with actual experience with the tools involved can shed some insight into how best to set this up.

I have a headless Ubuntu server running Hardy as up-to-date as possible.  I use it as an Internet filter, file server, and anything else that interests me at the time, but I do not need it as mail server since I have a hosted web domain that I trust more than I trust this old box.  However, I would like to delve into some more advanced administration projects and, as such, it would be nice to set it up for problem notification.

The most obvious approach that I can think of is to set it up as a complete mail server and then setup one account on it that forwards to one of my external email accounts.  It would seem, however, that if the server can be set to send a notification through an email account that it is hosting then it would also be able to set it up to send a notification through an email account that it is not hosting so that I can bypass setting up a whole email server that won't be used for anything else.

Does anyone that is familiar with the subject have any advice on how to set this up simply or maybe even a better approach?

---

### Post by sdnelson on 2008-11-25
Why not have the problem notification send an email to a local account on that server and in the aliases file add your external email account to it.

Example: /etc/aliases

root:   root, [email]me@myhost.com[/email]

Just a thought.

---

### Post by zenon212 on 2008-11-25
That sounds simple enough.

So do all accounts have email even if there is not an email server setup?

Thank you for the advice.

---

### Post by sdnelson on 2008-11-25
If you look at what's in /etc/passwd - most new users or current users have local email accounts. You can essentially have all of them forwarded to you or to your personal email address.

Good luck.

---

