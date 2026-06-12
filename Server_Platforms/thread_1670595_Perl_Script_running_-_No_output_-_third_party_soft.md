---
title: "Perl Script running - No output - third party software"
date: 2011-01-19
forum: Server Platforms
---

### Post by sivarajan on 2011-01-19
Hi,

I'm developing a server using CGI-perl. I'm a linux user. I made a CGI page nd i'm calling a perl script as a response to submit. I'm performing various tasks with in tat perl file using system() command, like given below

$cmd="perl [abc.pl]("http://abc.pl/") <input file>";
system($cmd);

When i tried to run a 3rd party software executable command (svm_classify) like this

$cmd="svm_classify <testfile> <modelfile> <outputfile>";
system($cmd);

the output file is not getting generated. but it says no error also.

Additional:
I tried to run that part alone as a perl script nd its working fine.
I tried to run that part from command line nd its working fine.

PLSSSSSSSS help me out!!!!!!!!!!

thanx a lot,
[COLOR=#888888]K. Sivarajan.[/COLOR]

---

