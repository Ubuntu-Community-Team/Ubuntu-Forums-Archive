---
title: "AD Integration and SSO encryption"
date: 2014-10-01
forum: Ubuntu, Linux and OS Chat
---

### Post by V3u5nbRjDF on 2014-10-01
Although I have a new ubuntuforums account, I've been around for a long time, first using ubuntu in the 4.10 days.

These are two things that I think would be great if they ever found a way into Ubuntu.

AD integration during the installation. I know it would be great if we all lived in a world where Windows AD was not the norm in business, but it is what it is. I think it would be great if AD integration were possible during the installation. It's not difficult with likewise-open, but it would be great if it could be integrated fully from the get go. One of the possible benefits to that would be that you could potentially leverage the integration into the encryption to allow for SSO. Meaning, when I decrypt the drive, it requests a username and a password, authenticates them against the AD, and if the user is in the right group, then it decrypts and signs in the user. This would also make it super easy to enforce account password changing and having it apply with the encryption as well, which should change periodically.

---

### Post by grahammechanical on 2014-10-01
Please explain "AD." I have no idea what it is. Proprietary code? If that is the case it is not going to happen.

How many users would need this? You say "the norm in business." But I am not in business. Why should having this from "the get go" interest me? Is this suggestion something that Ubuntu developers would describe as "not trivial?" In other words, it would take a lot of work and then might break things in the meantime.

---

### Post by PondPuppy on 2014-10-01
I didn't know either. I had to Google it: [http://en.wikipedia.org/wiki/Active_Directory](http://en.wikipedia.org/wiki/Active_Directory)

[FONT=sans-serif][COLOR=#252525]I'm ignorant of network admin. From the article linked: [/COLOR][/FONT]"Varying levels of interoperability with Active Directory can be achieved on most Unix-like operating systems (including Unix, Linux, Mac OS X or Java and Unix-based programs) through standards-compliant LDAP clients, but these systems usually do not interpret many attributes associated with Windows components, such as Group Policy and support for one-way trusts."

---

### Post by dataformsaction on 2014-10-01
Interesting, I didn't know Linux could interoperate so well with Active Directory (which is really just an LDAP directory)

But surely offering it as a post installation step would be just as good? I can't see any special need to add it to the installer.

>This would also make it super easy to enforce account password changing
Password changing policies used to be the bane of my life, thank goodness for smart cards which removed the need for that!

Enforcing frequent password changes are just an invitation for users to write it on a Post-it note and 'hide' it under their keyboard.

---

### Post by V3u5nbRjDF on 2014-10-01
Yes.  My apologies for using jargon and just noting it as applying to a "business" environment, as it is definitely not universal, but it is very common.  AD is the Active Directory and the use of LDAP authentication.  

It wouldn't be a requirement during install, however I think that having it as an option, particularly if the active directory authentication would be able to 

a) Be used for decryption of the device.
b) Be used for single sign on after the decryption
c) Probably to assign some level of permissions

I am absolutely with you, in that password changing policies can take up way more time than they should.  It, like using Active Directory for authentication is a reality for me and many others.

As for a home user, why would they want that?  They probably wouldn't, however for use in an environment that uses Active Directory (LDAP) for authentication, it would be a terrific option!  Especially one that also makes heavy use of full disk encryption.  Again, I don't want to advise that this is a default, but having it as an option would be terrific in any environment that is using Active Directory.

---

