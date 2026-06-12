---
title: "Ubuntu Advantage CIS scripts: locked out of workstation"
date: 2022-01-31
forum: Security
---

### Post by jyghm on 2022-01-31
I have just run the CIS level 1 script on a workstation and attempted to login. I entered the previous passphrase and was then informed i needed to change the password. However, the screen presented to me only asked for the current password. I entered this but it was rejected. 

I am now locked out. Furher attempts to login is logged and tells me I’m locked out due to too many failed login attempts.

Has anyone else found this issue too?

Will the lockout time out?

---

### Post by rstraub-3589 on 2022-05-06
Hey there,
I just registered to talk about CIS scripts and saw your thread.

I aswell found it counterintuitive but some things I noticed:
When running the fix, the authentification is checking a pam module "pwquality", which is not installed on a default LTS20.04.
Luckily I still had a open shell. So prior to applying the fix install the module "apt-get install libpam-pwquality".
Also, when changing your password the shell get's closed with an error but the password did in fact change.

And the third thing to be very cautios, is when setting a grub-superuser password, you will be required to enter that pw on each boot. To remediate:
Open and edit the file /etc/grub.d/10_linux and find the line "menuentry '$(echo "$os" | grub_quote)' ${CLASS}" , there, append the parameter " --unrestricted " behind "${CLASS}".

Best regards and good luck

---

