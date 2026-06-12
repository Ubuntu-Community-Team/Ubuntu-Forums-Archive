---
title: "XenCenter login failure to new XCP-XAPI box"
date: 2013-06-29
forum: Virtualisation
---

### Post by philled on 2013-06-29
I've done a fresh install of Ubuntu Server 12.04 and installed xen-hypervisor on top of that (as per [these instructions]("https://help.ubuntu.com/community/Setting%20up%20Xen%20and%20XAPI%20%28XenAPI%29%20on%20Ubuntu%20Server%2012.04%20LTS%20and%20Managing%20it%20With%20Citrix%20XenCenter%20or%20OpenXenManager")).

I already had XenCenter on my PC. When I try to add my new server in XenCenter I get an error in XenCenter "Incorrect username and/or password". I'm certain that I'm using the same username and password that I used in the Ubuntu install, and which successfully logs in over putty.

I found [one page]("https://7terminals.com/articles/fix-login-failure-from-xencenter-to-xcp-xapi-running-on-ubuntu-12-04/") that talked about updating /etc/pam.d/xapi but it looks like the formatting is messed up and I can't work out what it's supposed to say. It says to do this which looks like garbled nonsense to me:

[FONT=courier new]# echo -e “#%PAM-1.0nauthtincludetcommon-authnaccounttincludetcommon-authnpasswordtincludetcommon-auth” > /etc/pam.d/xapi”[/FONT]

Does anyone know what I need to do to get the login working from XenCenter? I can't use my new Xen installation without that.

---

### Post by philled on 2013-06-29
I've managed to de-garble the line in the /etc/pam.d/xapi file. If you change the file to look like this, you should be able to log in with XenCenter:

[FONT=courier new]#%PAM-1.0
auth include common-auth
account include common-auth
password include common-auth[/FONT]

Hope that helps someone who comes across a similar issue in future.

---

