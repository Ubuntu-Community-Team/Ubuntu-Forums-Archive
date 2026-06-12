---
title: "ISPconfig help"
date: 2006-02-14
forum: Server Platforms
---

### Post by vvnoob on 2006-02-14
Need help what is gone bad? Any ideas?Does anyone intalled ISPconfig on Breezy?


[HTML]+--------------------------------------------------------+
| You now have successfully built and installed the      |
| Apache 1.3 HTTP server. To verify that Apache actually |
| works correctly you now should first check the         |
| (initially created or preserved) configuration files   |
|                                                        |
|   /root/ispconfig/httpd/conf/httpd.conf
|                                                        |
| and then you should be able to immediately fire up     |
| Apache the first time by running:                      |
|                                                        |
|   /root/ispconfig/httpd/bin/apachectl start
|                                                        |
| Or when you want to run it with SSL enabled use:       |
|                                                        |
|   /root/ispconfig/httpd/bin/apachectl startssl
|                                                        |
| Thanks for using Apache.       The Apache Group        |
|                                [http://www.apache.org/](http://www.apache.org/)  |
+--------------------------------------------------------+
creating cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for AIX... no
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking for re2c... exit 0;
checking whether ln -s works... yes
checking for mawk... mawk
checking for bison... bison -y
checking bison version... configure: warning: You will need bison 1.28, 1.35, 1.75 or 1.875 if you want to regenerate the Zend parser (found 2.0).
2.0 (ok)
checking for flex... lex
checking for yywrap in -ll... no
checking lex output file root... ./configure: line 2422: lex: command not found
configure: error: cannot find output from lex; giving up
ERROR: Could not configure PHP
cd: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
mv: cannot stat `binaries/aps.tar.gz': No such file or directory
mv: cannot stat `binaries/spamassassin.tar.gz': No such file or directory
mv: cannot stat `binaries/uudeview.tar.gz': No such file or directory
mv: cannot stat `binaries/clamav.tar.gz': No such file or directory
mv: cannot stat `binaries/cronolog': No such file or directory
mv: cannot stat `binaries/cronosplit': No such file or directory
mv: cannot stat `binaries/ispconfig_tcpserver': No such file or directory
mv: cannot stat `binaries/zip': No such file or directory
mv: cannot stat `binaries/unzip': No such file or directory
tar: spamassassin.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `spamassassin': No such file or directory
tar: uudeview.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `uudeview': No such file or directory
tar: clamav.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `clamav': No such file or directory
tar: aps.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
./setup2: line 771: ispconfig_tmp/php/bin/php: No such file or directory
ERROR: The PHP binary coming with ISPConfig does not work properly on your system! The installation routine stops here![/HTML]

---

### Post by vvnoob on 2006-02-14
For those with same issue wiyh ISPconfig look here [http://www.howtoforge.com/forums/showthread.php?t=2500](http://www.howtoforge.com/forums/showthread.php?t=2500) here are answers u need.

Greetz 
vvnoob

---

