---
title: "Advanced problem, Unable to access to server"
date: 2010-08-27
forum: Server Platforms
---

### Post by loknar28 on 2010-08-27
I was setting up winbind and successfully joined the 10.04 server to our domain. I was able to see users and groups running wbinfo -u and -g. I was able to access shares on our network, but only could write to the shares when in sudo/root. I also was having issues consistently being able to login as a domain user.
I was going over configuration changes I had made through the process of setting all of this up and then left for lunch. 
The files I was looking through where the following.
/etc/samba/smb.conf 
/etc/nsswitch.conf
/etc/pam.d/common-account
/etc/pam.d/common-auth
/etc/pam.d/common-session
/etc/pam.d/sudo
The guide I was using is: [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

When I came back I could no longer login using my local account and the root account had not been set yet.

I entered recovery mode and managed to change the root password and my local account password but still neither would work to login.  

I am also using kubuntu if that effects anything.

---

### Post by craigp84 on 2010-08-27
Hi,

Boot from rescue and have a look at your /etc/nsswitch.conf again, it's the most likely think to have wrong.

From the pam side of things, assuming you followed that guide, as long as you didn't delete the "sufficent" for pam_unix, and you didnt set winbind as required, then pam will be fine.

---

### Post by loknar28 on 2010-08-27
I only added to these files, as I did not want to remove default values. I noticed this does end up with some duplication of entrys but it not seem to cause any issue at first
nsswitch.conf

```
passwd: compat winbind
group: compat winbind
shadow: compat winbind
```For pam none of the files have pam_winbind.so as required
common-auth
```
auth [success=2 default=ignore]  pam_unix.so  nullok_secure
auth [success=1 default=ignore]  pam_winbind.so krb5_auth krb_ccache_type=FILE cached_login try_first_pass
auth requisite  pam_deny.so
#
auth requisite  pam_deny.so
#
#
#
auth sufficient  pam_unix.so nullok_secure
auth sufficent  pam_winbind.so require_membership_of=domain^admins use_first_pass
auth  requisite  pam_deny.so
auth required  pam_permit.so
#
auth optional  pam_ecryptfs.so unwrap
#
```common-account
```
account  [success=2 new_authtok_reqd=done default=ignore]   pam_unix.so
account  [success=1 new_authtok_reqd=done default=ignore]   pam_winbind.so
#
account requisite  pam_deny.so
#
#
#
account sufficient  pam_winbind.so
account required pam_unix.so
#
#

```common-session
```
session [default=1]   pam_permit.so
#
session requisite  pam_deny.so
#
#
#
session required  pam_permit.so
#
session required  pam_unix.so
session required  pam_mkhomedir.so umask=0022 skel=/etc/skel
session optional  pam_winbind.so
session optional  pam_ecryptfs.so unwrap
session optional  pam_ck_connector.so nox11

```sudo
```
auth sufficient pam_winbind.so
auth sufficient pam_unix.so use_first_pass
auth required pam_deny.so

@include common-auth
@include common-account

session required pam_permit.so
session required pam_limits.so

```> **craigp84 said:**
> Hi,

Boot from rescue and have a look at your /etc/nsswitch.conf again, it's the most likely think to have wrong.

From the pam side of things, assuming you followed that guide, as long as you didn't delete the "sufficent" for pam_unix, and you didnt set winbind as required, then pam will be fine.

---

### Post by craigp84 on 2010-08-27
I tempted fate huh :)

Your nsswitch is fine.

Your PAM isn't though. Can you get rid of all the pam_deny lines in your common-* and your sudo too.

On top of that, strip out all lines with square brackets on.

That will leave a much more sane looking PAM config :-)

---

### Post by loknar28 on 2010-08-30
That fixed the problem. Thank you so much for your help. Are there any security concerns with leaving out the deny lines completely?
Also, whenever I log into the machine as a domain user I get a message that says, "Cannot convert group doamin^admins to sid, please contact your administrator to see if group domain^admins is valid."
I changed the line in /etc/pad.d/common-auth to say domain^users and I get the same message, except now the error references domain^users 
I just now started also receiving an error that says "kstartupconfig4 does not exist or fails."
"The error code is 3. Check your installation."
Then it fails back to the login prompt.
Collin

---

### Post by craigp84 on 2010-08-31
Hi,

pam_deny.so is generally for specialised use in more complex scenarios. You're not loosing anything security wise dropping those out (they didn't make sense to have in your config).

For the winbind group -> sid resolution, can you paste the output exactly of a "wbinfo -g | grep -i domain | grep -i admin"

---

