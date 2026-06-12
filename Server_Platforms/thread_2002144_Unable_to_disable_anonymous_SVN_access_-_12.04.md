---
title: "Unable to disable anonymous SVN access - 12.04"
date: 2012-06-12
forum: Server Platforms
---

### Post by fcdev on 2012-06-12
I am currently trying to configure a SVN server to prohibit any  anonymous access, I'm following all the tutorials I can find, and  everything tells me to do what I have already done, and I can still  access (read) the repository in anonymous mode (both via tortoise SVN on  Windows, and via HTTP).

I am running from a vanilla install of Ubuntu 12.04 LTS, and have svnserve 1.6.17 installed.

/etc/apache2/mods-available/dav_svn.conf looks like this ...
<Location /svn>
     DAV svn
     SVNParentPath /home/svn
     SVNListParentPath On
     AuthType Basic
     AuthName "Subversion Repository"
     AuthUserFile /etc/subversion/passwd
     <LimitExcept GET PROPFIND OPTIONS REPORT>
        Require valid-user
     </LimitExcept>
  </Location>

I have tried removing /etc/passwd to see if that would help, but it doesn't.  It looks like this ...
steve:$apr1$Y130T/Sc$CL2a5.A5MGUCgx.C9kSHj2

/home/svn/testSVN/conf/svnserve.conf looks like this ...
[general]
anon-access = none
auth-access = write
password-db = passwd
realm = testSVN_realm

and /home/svn/testSVN/conf/passwd looks like this ...
[users]
bob = bob

Additionally, when I do try to write to the SVN server, it only accepts my 'steve' credentials, not the 'bob' credentials.

I don't care if I have to access it via HTTP or via command prompt, or  whatever, I just need to disable anonymous access.  Can anyone tell me  what I'm doing wrong?  Any help would be greatly appreciated.

- Stephen Fraser

---

