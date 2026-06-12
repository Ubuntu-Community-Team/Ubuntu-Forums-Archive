---
title: "cron stoped sending mails"
date: 2011-06-07
forum: Server Platforms
---

### Post by rodrigomartinho on 2011-06-07
Hello.

I have a Ubuntu Server 11.04 x64. My emails are sent via ssmtp.

Everything worked fine, but cron stopped sending emails.

ssmtp is working, as I can see by testing it on terminal (echo "Test"|mail -s "Test" [EMAIL="user@gmail.com"]user@gmail.com[/EMAIL]). I didn't make any change in ssmtp config.

cron is working too, I have made tests to ensure about it, it only isn't sending emails. I also tried the MAILTO option, which shouldn't be necessary, but didn't work either.

Looking at mail.log, it seems it stopped working in june, 1st, maybe after some upgrade, but I'm not sure about that.

Any clue?

Thanks in advance,

Rodrigo Martinho.

---

### Post by rodrigomartinho on 2011-06-07
I have two almost identical servers running in diferent places. I searched my emails received from both, and I stopped receiving cron emails in both after this upgrade:

apticron report [Mon, 30 May 2011 16:28:10 -0300] ========================================================================  apticron has detected that some packages need upgrading on:  	server.rodrigo.local  	[ 127.0.1.1 192.168.0.100 192.168.0.100 ]  The following packages are currently pending an upgrade:  	bind9 1:9.7.3.dfsg-1ubuntu2.1 	bind9-host 1:9.7.3.dfsg-1ubuntu2.1 	bind9utils 1:9.7.3.dfsg-1ubuntu2.1 	dnsutils 1:9.7.3.dfsg-1ubuntu2.1 	libbind9-60 1:9.7.3.dfsg-1ubuntu2.1 	libdns69 1:9.7.3.dfsg-1ubuntu2.1 	libisc62 1:9.7.3.dfsg-1ubuntu2.1 	libisccc60 1:9.7.3.dfsg-1ubuntu2.1 	libisccfg62 1:9.7.3.dfsg-1ubuntu2.1 	liblwres60 1:9.7.3.dfsg-1ubuntu2.1 	libpam0g 1.1.2-2ubuntu8.2 	libpam-modules 1.1.2-2ubuntu8.2 	libpam-modules-bin 1.1.2-2ubuntu8.2 	libpam-runtime 1.1.2-2ubuntu8.2  ========================================================================  Package Details:  Lendo logs de mudanças... --- Mudanças para bind9 (bind9 bind9-host bind9utils dnsutils libbind9-60 libdns69 libisc62 libisccc60 libisccfg62 liblwres60) --- bind9 (1:9.7.3.dfsg-1ubuntu2.1) natty-security; urgency=low    * SECURITY UPDATE: denial of service via off-by-one     - lib/dns/ncache.c: correctly validate length.     - Patch backported from 9.7.3-P1.     - CVE-2011-1910   -- Marc Deslauriers [EMAIL="marc.deslauriers@ubuntu.com"]<marc.deslauriers@ubuntu.com>[/EMAIL]  Fri, 27 May 2011 12:50:40 -0400  --- Mudanças para pam (libpam0g libpam-modules libpam-modules-bin libpam-runtime) --- pam (1.1.2-2ubuntu8.2) natty-security; urgency=low    * SECURITY UPDATE: multiple issues with lack of adequate privilege     dropping     - debian/patches/security-dropprivs.patch: introduce new privilege       dropping code in libpam/pam_modutil_priv.c, libpam/Makefile.*,       libpam/include/security/pam_modutil.h, libpam/libpam.map,       modules/pam_env/pam_env.c, modules/pam_mail/pam_mail.c,       modules/pam_xauth/pam_xauth.c.     - CVE-2010-3430     - CVE-2010-3431     - CVE-2010-3435     - CVE-2010-4706     - CVE-2010-4707   * SECURITY UPDATE: privilege escalation via incorrect environment     - debian/patches/CVE-2010-3853.patch: use clean environment in       modules/pam_namespace/pam_namespace.c.     - CVE-2010-3853   * debian/patches-applied/series: disable hurd_no_setfsuid patch, as it     isn't needed for Ubuntu, and it needs to be rewritten to work with the     massive privilege refactoring in the security patches.   -- Marc Deslauriers [EMAIL="marc.deslauriers@ubuntu.com"]<marc.deslauriers@ubuntu.com>[/EMAIL]  Thu, 19 May 2011 08:40:22 -0400  pam (1.1.2-2ubuntu8.1) natty-proposed; urgency=low    * debian/patches-applied/update-motd: santize the environment before     calling run-parts, LP: #610125   -- Dustin Kirkland [EMAIL="kirkland@ubuntu.com"]<kirkland@ubuntu.com>[/EMAIL]  Wed, 27 Apr 2011 13:02:15 -0500  ========================================================================  You can perform the upgrade by issuing the command:  	aptitude full-upgrade  as root on server.rodrigo.local  -- apticron


maybe I stopped recieving all system emails, but I am sure only about cron right now.

---

### Post by rodrigomartinho on 2011-06-09
I have made some more tests and notice I was messing some things up.

Firstly,  cron wasn't working as should. As I could find searching other forums,  cron really had a problem after upgrades in pam packages. A restart in  cron solved this.

The email problem is a diferent one. After cron  restart, emails started being sent again. But only from root user. Cron  jobs from other users aren't sending emails, even with MAILTO=root  option.

Maybe I am missing something about ssmtp, and it has  nothing to do with cron. But I am not sure about it. I set up another  user on revaliases, but cron still doesn´t send emails. Looking at  syslog, I see that ssmtp stops at:

SSL connection using RSA_ARCFOUR_SHA1

Any help?

---

### Post by rodrigomartinho on 2011-06-13
I did no changes, and server just started sending emails again, even for users other than root. I don't know why, but it is working.

---

