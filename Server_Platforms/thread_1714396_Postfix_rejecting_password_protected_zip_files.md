---
title: "Postfix rejecting password protected zip files"
date: 2011-03-25
forum: Server Platforms
---

### Post by NorthstarTX on 2011-03-25
I recently set up a machine with Ubuntu 10.4 LTS to help to replace an aging VAX mailserver that was the DMZ mailserver for the company I work for. I set up a default install of postfix (via apt-get) to function as a DMZ border device that routes between two internal mailservers based on subdomain aliasing via internal DNS.

The problem is that although I have installed no anti-spam or anti-virus options, mail sent to this machine from any outside source containing a password-protected zip file is being rejected with error:

552 Password protected zip file found inside of the email

At first I'd thought that possibly it was the sending mailserver issuing this error, but after further testing I found that no matter the source, any password protected zip file is immediately rejected. Being as we're in a HIPAA-sensitive environment, this has been relied upon as a backup for people to do one time encrypted file sends via email. The file in question is relatively small, and I do not have any quotas on, and the same test file sent two ways (one encrypted zip and one non-encrypted zip) caused the encrypted zip only to fail.

As stated before, I do not use any type of antivirus or antispam measures, no header or body checks have been put in place, and in the course of trying to troubleshoot this problem, have probably opened my server up more than is strictly wise. I really need to enable this feature as being unable to take encrypted zips puts the entire migration at risk. Any suggestions?

---

### Post by SeijiSensei on 2011-03-25
> **NorthstarTX said:**
> Being as we're in a HIPAA-sensitive environment, this has been relied upon as a backup for people to do one time encrypted file sends via email.

I don't know how Postfix handles this, but I consult to a health center where we run MailScanner which filters password-protected ZIPs as well.  Our solution is to let only a few designated IT admins receive these messages directly.  Any others go to quarantine where they can be released by an admin if they're found to be legitimate.  

I'd recommend taking a look at [MailScanner]("http://www.mailscanner.info/") which you can install on top of Postfix.  It is very configurable.  For instance, you can permit a password-protected ZIP if it doesn't contain another such file.  Nearly every filter can also be configured on a per-sender or per-recipient basis, so if you know in advance who's sending legitimate ZIPs you can whitelist them.

---

