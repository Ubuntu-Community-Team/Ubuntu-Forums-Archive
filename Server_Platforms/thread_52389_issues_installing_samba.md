---
title: "issues installing samba"
date: 2005-07-27
forum: Server Platforms
---

### Post by Buddha_Joe on 2005-07-27
I am  trying to get samba installed on one of my boxes and I get the following while running apt-get:


```

Setting up samba (3.0.14a-3ubuntu3~5.04ubp1) ...
TDBSAM version too old (0), trying to convert it.
TDBSAM converted successfully.
account_policy_get: tdb_fetch_uint32 failed for field 1 (min password length), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 2 (password history), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 3 (user must logon to change password), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 4 (maximum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 5 (minimum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 6 (lockout duration), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 7 (reset count minutes), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 8 (bad lockout attempt), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 9 (disconnect time), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 10 (refuse machine password change), returning 0

```

I can't seem to find any information on this on google, (at least not in english) and I was wondering if anybody here has run across it before.. I have another machine running ubuntu server running samba fine and I followed the same steps outlined at the unofficial ubuntu guide for both machines.

I continued with my configuration and when I tried to mount the share via fstab I get the following error

```

31816: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

```

Mind you I have no issues connecting to the other server using the same method. I have compared the smb.conf files on both machines and I dont see any diffrences. The only thing I can think of as causing the authentication problem is related to  what ever the problem was creating the tdbsam during the install.

Now I know I will be showing my windows roots here but I did uninstall samba and removed all of the related tdb files and resintalled it but I ran across the same issue.  I even removed samba, ran apt-get dist-upgrade and tried again but to no avail.

any ideas would be greatly appreciated.

---

### Post by Buddha_Joe on 2005-07-27
figured it out.. The error messages during the install were not creating a problem. it turns out that I had to enable the user accounts for samba using **sudo smbpasswd -e [username]**

---

