---
title: "Quick way of sharing files securely through Samba with single username/password?"
date: 2008-03-22
forum: Security Discussions
---

### Post by Yfrwlf on 2008-03-22
I am going to make a guide for easily sharing files through Samba in a secure way using a SINGLE user and password, once I find out how, so that other users can do this.  I feel this is important for the following scenarios:

1.  You want to share out some files, but don't want just anyone to read them.

2.  You want to share out some files that are writable to authorized users so they can upload, but do not want just anyone to be able to write or especially to delete them.

3.  You want to prevent BOTH Windows and Linux users from being able to have access to those files without first providing the user name and password.

4.  You do not want to add a user account for every single user who wants to access the files, but instead wish to have one user name and password to make administration easy.

By default from a Ubuntu install, Samba is configured to allow other Ubuntu/Linux machines to freely have access to Samba shares, yet Windows users need to put in a user name and password.  I think they can specify the account "nobody" with no password and that will work.  This account seems to be the one that Samba uses by default, and yet at the same time, it doesn't...even with the "nobody" Samba account deleted, Ubuntu machines are still able to view shares with the "public" setting, so they must be using a different account?  No clue.

Regardless, what I want to do is change this setup to one that requires a **single** Samba user name and password that is **required** by **all** machines in order to access the files and thus be secure.  I also want this to be the only Samba account, or quite simply, the only point of entry for security.

I've tried numerous settings in smb.conf including:

For the global section:

security = user
guest account
map to guest

For the shares section:

public
guest only
guest ok
force user
valid users

No amount of playing with these has achieved my goal.  No amount of perusing through the Samba docs has helped me to get this working.  If I turn public to no, I am never asked for a password from Ubuntu machines and instead am simply denied until I change this setting to yes.

If I could simply have a "guest account" and require all shares to be shared under this single account, and then give that account a password, that would be fine.  If the solution is to not use a guest account, and instead create a single user, awesome.

Does anyone know how to do either of these things?  So far all attempts have failed and the only things I've achieved are to either make everything totally open, or totally broken.  An easy way to securely share files would be great.

---

### Post by HermanAB on 2008-03-23
Here you go:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

Cheers,

Herman

---

### Post by nutz on 2008-03-23
It is easier to just use the smbpasswd command to set a password.

---

