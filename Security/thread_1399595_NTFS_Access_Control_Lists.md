---
title: "NTFS Access Control Lists"
date: 2010-02-05
forum: Security
---

### Post by user2037 on 2010-02-05
Does Ubuntu's NTFS-3G package include support for NTFS ACL's when a mapping file is present?

---

### Post by yogesh.girikumar on 2010-02-08
Hi,
       The following text is from the home site of the ntfs-3g project.[INDENT]> Access Handling and Security

       By default, files and directories are owned by the effective user and group of the mounting process and everybody has full read, write, execution and directory browsing permissions. You can also assign permissions to a single user by using the uid and/or the gid options together with the umask, or fmask and dmask options.

       Doing so, Windows users have full access to the files created by ntfs-3g.

       But, by defining a Windows-to-Linux user mapping in the file .NTFS-3G/UserMapping, you can benefit from the full ownership and permissions features as defined by Posix and those ownership and permissions will be applied to Windows users and conversely.

       If ntfs-3g is set setuid-root then non-root users will be also able to mount volumes.
[/INDENT]Run the following command in the terminal to find out more about ntfs-3g```
$ man ntfs-3g
```      Please see:
       
[LIST=1]
[*][http://www.tuxera.com/community/ntfs-3g-advanced/ownership-and-permissions/#options](http://www.tuxera.com/community/ntfs-3g-advanced/ownership-and-permissions/#options)
[/LIST]
       
[LIST=1]
[*][http://www.tuxera.com/community/ntfs-3g-manual/](http://www.tuxera.com/community/ntfs-3g-manual/)
[/LIST]
       
[LIST=1]
[*][http://www.tuxera.com/community/ntfs-3g-faq/](http://www.tuxera.com/community/ntfs-3g-faq/)
[/LIST]
Hope this is helpful.

---

### Post by user2037 on 2010-02-09
There is no sign of the user mapping utility in Ubuntu's NTFS-3G package. So my guess is that feature isn't yet included.

Regardless, NTFS-3G's implementation is too resource intense for my device so I'm going to try a different solution.

---

### Post by yogesh.girikumar on 2010-02-17
Hi,


       There IS a user mapping utility for Linux which is included in the ntfs-3g package. Ubuntu does not bundle the latest version of ntfs-3g package. The latest version is **ntfs-3g - 2010.1.16**

       You can find the version of the ntfs-3g package currently installed in your system by executing the following command in the terminal
   ```
$ sudo apt-cache showpkg ntfs-3g | less
```  The usermapping utility is started by running the command :
```
$ sudo ntfs-3g.usermap
```      This utility comes bundled with the latest version of ntfs-3g package, the source code of which you can download and compile it yourself.


       **Step 1:** Download the code from this page: [http://www.tuxera.com/community/ntfs-3g-download/](http://www.tuxera.com/community/ntfs-3g-download/) . Download the most stable version available. When I write this post, it's 2010.1.16


       **Step 2:** Extract the archive and compile it. To do so, execute the following lines of code one after the other:


 Let's assume that the ntfs-3g source tar file ( named something like "ntfs-3g-2010.1.16.tgz" ) has been downloaded to /home/username/Downloads,
```
$ cd /home/username/Downloads
$ tar xvzf ntfs-3g-2010.1.16.tgz
$ cd ntfs-3g-2010.1.16
$ ./configure
$ make
$ make install
```      If you want a more customized installation, read the "README" and "INSTALL" files located inside the ntfs-3g-2010.1.16 directory under /home/username/Downloads.


   **Step 3:** Now you will be able to run the command
```
$ sudo ntfs-3g.usermap
```      Now follow the instruction on this page to perform usermapping in Ubuntu: [http://pagesperso-orange.fr/b.andre/usermap.html](http://pagesperso-orange.fr/b.andre/usermap.html)
[URL="http://pagesperso-orange.fr/b.andre/usermap.html"]
[/URL]
       NOTE: The command to execute is given as just "usermap". But you have to run "ntfs-3g.usermap". See the man page for ntfs-3g.usermap for more information on this command. 

       

NOTE: The windows utility link is broken. You can download it from here: [http://pagesperso-orange.fr/b.andre/advanced-ntfs-3g.html](http://pagesperso-orange.fr/b.andre/advanced-ntfs-3g.html)


Hope this helps

---

