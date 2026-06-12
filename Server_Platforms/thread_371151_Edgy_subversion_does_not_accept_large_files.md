---
title: "Edgy subversion does not accept large files"
date: 2007-02-26
forum: Server Platforms
---

### Post by andreseso on 2007-02-26
Hello,

I had a server running Mandriva 2007.  I made a subversion repository of all my documents.  After using Ubuntu at home and at work for several months, I decided to install Ubuntu on my server.  I basically wanted a LAMP server with subversion.

From the start I have had huge problems with the subversion installed on Ubuntu Edgy. Apart from being a quite old version, both subversion and apache2 are linked with libapr-0.  libapr-0 has a file size limit of 2 GB.  My subversion dump was 2.2 GB so I had to bend over backwards to import my repository into subversion.  Basically I had to compile subversion 1.3.2 linked with libapr1 which does not have these file size limits.

My repository is working correctly.  The only problem is that my first revision is 2.1 GB in size.  That makes it impossible for Edgy's subversion to work with it.  I can add files to the repository and commit files.  However it fails miserably when I modify a file that was added in revision 1.  Due to libapr0's limitations with file sizes and my 2.1 GB first revision, **svn ci** fails with the error message 
```
svn: Commit failed (details follow):
svn: Can't open file '/home/svn/repo/db/revs/1'

```

It is inconvenient for me having a subversion repository I only can add new files to.  I would much prefer having as well the possibility of modifying existing files.

For my repository to work I would have to link both subversion and apache2 to libapr1.  I access subversion through apache.  I could recompile, but to satisfy the dependencies of my LAMP + svn server I would have to recompile php from a tarball. I find compiling php really messy.

Can you think of a workaround which would allow me to use Ubuntu Edgy's subverion?

```
 ldd /usr/bin/svnadmin 
        libapr-0.so.0 => /usr/lib/libapr-0.so.0 (0xb7f4f000)
        libaprutil-0.so.0 => /usr/lib/libaprutil-0.so.0 (0xb7db3000)

```
```
 ldd /usr/sbin/apache2
        libaprutil-0.so.0 => /usr/lib/libaprutil-0.so.0 (0xb7da2000)
        libapr-0.so.0 => /usr/lib/libapr-0.so.0 (0xb7c45000)

```

---

### Post by andreseso on 2007-03-11
Hello,

As I stated previously the subversion package that comes with Ubuntu Edgy is useless for me as it is linked with libapr0 which in turn imposes a 2 GB limit on the files accessed and I have a 2.1  GB file in my repository.

I must admit that the simplest solution for me would be for the Ubuntu Edgy package maintainers to release subversion packages where subversion 1.3.2 and all its dependencies are linked with libapr1 instead of libapr0.  I would like to get in touch with them to find out if it were possible.

If not, I could always download all the deb sources and try to modify them to change the dependencies and the libraries they are linked with.  The problem is that I have never built a deb package and I am clueless how to change the dependencies of a package and the libraries with which it is linked.

Any suggestions on were to turn for further guidance?  Any suggestions on how to get in touch with the Ubuntu Edgy deb mantainers?

---

### Post by elst on 2007-03-11
I'd suggest checking whether the same issue exists with Feisty. This is due in April, so if it meets your needs then upgrading might be the simplest solution. If not then consider filing a bug report on Launchpad as a first step. You could also enquire on the Backports forum for third-party packages.

AIUI, the general policy is to avoid making changes to a version after release, except when necessary for security or stability, so this issue probably wouldn't be sufficient to warrent a general release of new packages for Edgy.

Of course, you are absolutely free to compile from source as well - you don't need to make packages to build an application from source.

---

