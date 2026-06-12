---
title: "OpenSSH 8.0"
date: 2019-04-26
forum: Ubuntu, Linux and OS Chat
---

### Post by Trevor_White on 2019-04-26
Hi all,
Quick question does anyone know if/when Ubuntu Server will support the latest OpenSSH 8.0 in it's LTS Products and if so will Trusy also be updated (as it's very close to its EOL)

I've looking to get this SCP vulnerability patched.

[https://www.theregister.co.uk/2019/01/15/scp_vulnerability](https://www.theregister.co.uk/2019/01/15/scp_vulnerability)

[https://www.openssh.com/txt/release-8.0](https://www.openssh.com/txt/release-8.0)

Many thanks.

---

### Post by QIII on 2019-04-26
Hello!

One might as well consider Trusty deceased, as it is but a matter of days until it expires.  Move on.

Will openSSH 8.0 be added to Trusty?  No.  I reckon it won't likely be added to any of the other currently supported LTS releases unless Canonical deems it to be a necessary security update.  Package versions are fixed prior to the release dates of every Ubuntu release and only updates to those package versions are made available -- unless a newer release is deemed necessary for security purposes.  In this case it may -- but only if there is not a patch available for the previous version.

That is, if Foobar 3.5 was available at the time 18.04 was released, when Foobar 4.0 comes out it would generally not be available to any previous Ubuntu release via Canonical's repos.  If Foobar 3.5.1 comes out sometime during the life of 18.04, it would likely be available.

---

### Post by Trevor_White on 2019-04-26
Many thanks for the quick reply and explanation, the only reason I mentioned Trusty is because we have a lot of Trusty servers in the field which we are slowly upgrading to Bionic but because there is no easy way to automate it, the process is taking a bit of time.

---

### Post by Morbius1 on 2019-04-26
For the specific security issues in your link I think we are covered with the version we have. This is the changelog to the the version I currently have in Xubuntu 18.04:
> openssh (1:7.6p1-4ubuntu0.3) bionic-security; urgency=medium

  * SECURITY UPDATE: Incomplete fix for CVE-2019-6111
    - debian/patches/CVE-2019-6111-2.patch: add another fix to the filename
      check in scp.c.
    - **CVE-2019-6111**
  * Fixed inverted CVE numbers in patch filenames and in previous
    changelog.

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Mon, 04 Mar 2019 07:17:51 -0500

openssh (1:7.6p1-4ubuntu0.2) bionic-security; urgency=medium

  * SECURITY UPDATE: access restrictions bypass in scp
    - debian/patches/CVE-2018-20685.patch: disallow empty filenames
      or ones that refer to the current directory in scp.c.
    - **CVE-2018-20685**
  * SECURITY UPDATE: scp client spoofing via object name
    - debian/patches/CVE-2019-6111.patch: make sure the filenames match
      the wildcard specified by the user, and add new flag to relax the new
      restrictions in scp.c, scp.1.
    - **CVE-2019-6111**
  * SECURITY UPDATE: scp client missing received object name validation
    - debian/patches/CVE-2019-6109-1.patch: sanitize scp filenames via
      snmprintf in atomicio.c, progressmeter.c, progressmeter.h,
      scp.c, sftp-client.c.
    - debian/patches/CVE-2019-6109-2.patch: force progressmeter updates in
      progressmeter.c, progressmeter.h, scp.c, sftp-client.c.
    - **CVE-2019-6109**

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Thu, 31 Jan 2019 08:58:34 -0500

---

### Post by Trevor_White on 2019-04-26
Perfect thanks, I didn't think about searching for the CVE, seems they fixed it in Trusty as well, awesome, and they released before OpenSSH.

[https://people.canonical.com/~ubuntu-security/cve/2018/CVE-2018-20685.html](https://people.canonical.com/~ubuntu-security/cve/2018/CVE-2018-20685.html)

[https://usn.ubuntu.com/3885-1/](https://usn.ubuntu.com/3885-1/)

---

