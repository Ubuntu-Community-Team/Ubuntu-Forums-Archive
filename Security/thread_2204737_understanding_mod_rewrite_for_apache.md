---
title: "understanding mod_rewrite for apache"
date: 2014-02-10
forum: Security
---

### Post by pedenski on 2014-02-10
hello. after reading several articles about **mod_rewrite **or **reverse proxying** im still really confused about it. given the fact im still learning about server administration.

to simply explain my situation, i have this webserver, and this server contains 1 website only which can be accessed by 
http://<some ip>/website

i gave this website to some security dept. for vulnerability scanning and was told that i need to configure my **mod_rewrite **rules. my question is how? 

he gave me a document exactly similar to this [http://seclists.org/fulldisclosure/2011/Oct/232](http://seclists.org/fulldisclosure/2011/Oct/232)

the document suggests to apply a patch [http://www.apache.org/dist/httpd/patches/apply_to_2.2.21/](http://www.apache.org/dist/httpd/patches/apply_to_2.2.21/)

*currently my apache version is :*
```
*Server version: Apache/2.2.22 (Ubuntu)*
[I]Server built:   Mar  8 2013 15:53:09
[/I]
```

or update configuration to something like

```
*RewriteRule /(.*)\.(jpg|gif|png)    [http://images.example.com/$1.$2](http://images.example.com/$1.$2) [P]*
```

im assuming, since im using the 2.2.22, patch seems to be unnecessary anymore which leaves me to the configuration.

where and how do i change my **RewriteRules**

---

### Post by sandyd on 2014-02-10
moved to security discussions

---

### Post by fugu2 on 2014-02-13
I havn't played around with apache enough recently to know exactly where your 'rewrite rules' are located, but you can find them yourself with
```
$ find /etc/apache -type f -exec grep -l -i 'RewriteRule' '{}' \;

```
This will list all of the files that are in your /etc/apache directory that contain the word 'RewriteRule'. Its probably gonna be in some directory named 'sites-available'. Its at least a start on how to fix your problem.

---

### Post by Habitual on 2014-02-14
As I have answered this very question on another forum, if [my answer]("http://www.linuxquestions.org/questions/linux-server-73/understading-mod_rewrite-for-apache-4175494404/#post5116909") is inadequate, or incorrect, I would appreciate knowing that it is deficient in any regard.
I take my fung.fu seriously.

Or.... you could just be "fact checking" my answer? Which I got from [here...]("http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html")

---

