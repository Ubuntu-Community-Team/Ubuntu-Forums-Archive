---
title: "libreoffice runs only with sudo"
date: 2011-08-18
forum: System76 Support
---

### Post by flo1805 on 2011-08-18
hy, I hope its the right place to post my problem.

my libreoffice doesn`t work any more. if I run it like:

```
florian@system:~$ libreoffice 
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'
florian@system:~$
```I always get that message. 
If I try it with sudo, it work`s fine.

Here is, how I tried to fix it:

remove libreoffice and reinstall
checked the rights of ~/.libreoffice/
removed ~/.libreoffice
checked out, if there is any openoffice.org file or dir on my system (none)

can someone help me please??
thanks

---

### Post by sanderd17 on 2011-08-18
Can you create a new user and try as that new user?

---

### Post by flo1805 on 2011-08-18
sorry..i forgot to write this option:

so, I made a new user and tried out.

result:

if I add a new user, it works until I reboot the system. afterwards I have the same problems with the new user.

---

### Post by sanderd17 on 2011-08-18
Very weird.

If you have the time, what happens if you reboot before you tried libreoffice? Are you able to start libreoffice after the reboot in that way? (btw, if you remove the user, make sure you also remove the users home directory)

For more serious debugging, can you make a stack trace as described here: [http://wiki.documentfoundation.org/BugReport#How_to_get_strace_log_.28on_Linux.29](http://wiki.documentfoundation.org/BugReport#How_to_get_strace_log_.28on_Linux.29)

Since the crash is in the beginning, I don't need compression would be needed, but that's up to you to decide.

---

### Post by flo1805 on 2011-08-18
ok..this is very crazy...

1. I added a new user
2. system reboot
3. login as the new user, libreoffice works great
4. system reboot
5. login as the new user, libreoffice works great

:confused:

---

### Post by Elfy on 2011-08-18
I would also wonder if at some point you've started libreoffice as root with sudo and that's causing the issue. 

Try removing the libreoffice folder from the home causing issue again. 

Then run libreoffice.

---

### Post by flo1805 on 2011-08-18
I removed .libreoffice from the home. 
Then I restarted the system and tried to run libreoffice....same problem again

---

### Post by Elfy on 2011-08-18
dp you get the same error with this for example 

libreoffice -calc

---

### Post by flo1805 on 2011-08-18
yes, same error..

---

### Post by Hagar Delest on 2011-08-18
You can try to install with the debs from the LibO website. See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68) the same procedure applies.

---

### Post by flo1805 on 2011-08-18
but this is open office, isn't it?

btw, I tried to install with the .rpm packages...

---

### Post by Hagar Delest on 2011-08-18
Yes, the procedure is for OOo but replace it with LibO and it's the same. With the autocompletion of the terminal, you don't even have to type the whole file names.

Don't use the RPM of course. Ubuntu is Debian-based...

---

### Post by flo1805 on 2011-08-18
yes, I know. I moved the rpm to debian with alien.

so as I read your link carefully, I tried to do.

```

florian@system:~$ sudo apt-get purge libreoffice* openoffice*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libreoffice-writer' for regex 'libreoffice*'
Note, selecting 'libreoffice-calc' for regex 'libreoffice*'
Note, selecting 'libreoffice-impress' for regex 'libreoffice*'
Note, selecting 'libreoffice-kde' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-oxygen' for regex 'libreoffice*'
Note, selecting 'libreoffice-base' for regex 'libreoffice*'
Note, selecting 'libreoffice-core' for regex 'libreoffice*'
Note, selecting 'libreoffice-base-core' for regex 'libreoffice*'
Note, selecting 'libreoffice-java-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-gcj' for regex 'libreoffice*'
Note, selecting 'libreoffice-report-builder' for regex 'libreoffice*'
Note, selecting 'libreoffice-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-default' for regex 'libreoffice*'
Note, selecting 'libreoffice-style' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-hicontrast' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-tango' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-crystal' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-human' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-andromeda' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-galaxy' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-industrial' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-us' for regex 'libreoffice*'
Note, selecting 'libreoffice-dev' for regex 'libreoffice*'
Note, selecting 'libreoffice-draw' for regex 'libreoffice*'
Note, selecting 'libreoffice-evolution' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-so52' for regex 'libreoffice*'
Note, selecting 'libreoffice-gnome' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk' for regex 'libreoffice*'
Note, selecting 'libreoffice-officebean' for regex 'libreoffice*'
Note, selecting 'libreoffice-bundled' for regex 'libreoffice*'
Note, selecting 'libreoffice-dbg' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-binfilter' for regex 'libreoffice*'
Note, selecting 'mozilla-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-ogltrans' for regex 'libreoffice*'
Note, selecting 'libreoffice-dev-doc' for regex 'libreoffice*'
Note, selecting 'libreoffice-dtd-officedocument1.0' for regex 'libreoffice*'
Note, selecting 'libreoffice-emailmerge' for regex 'libreoffice*'
Note, selecting 'libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk-gnome' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-3.3.2' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-gb' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-gb' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-us' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pt-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pt-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sv' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sv' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zh-tw' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zh-tw' for regex 'libreoffice*'
Note, selecting 'libreoffice-kab' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-3.3.2' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ast' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ast' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-be-by' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-be-by' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-ctl-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-or' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ta' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-te' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ku' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ku' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ns' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ns' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-or' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-rw' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-rw' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-si' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-si' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ss' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ss' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-st' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-st' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ta' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-te' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tg' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tg' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-th' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-th' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ts' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ts' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ug' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ug' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-uk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-uk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-uz' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-uz' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ve' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ve' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-vi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-vi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-xh' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-xh' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zu' for regex 'libreoffice*'
Note, selecting 'libreoffice-math' for regex 'libreoffice*'
Note, selecting 'libreoffice-nlpsolver' for regex 'libreoffice*'
Note, selecting 'libreoffice-voikko' for regex 'libreoffice*'
Note, selecting 'libreoffice-hyphenation-fi' for regex 'libreoffice*'
Note, selecting 'docvert-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-report-builder-bin' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-mobiledev' for regex 'libreoffice*'
Note, selecting 'openclipart-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-mysql-connector' for regex 'libreoffice*'
Note, selecting 'libreoffice-pdfimport' for regex 'libreoffice*'
Note, selecting 'libreoffice-presentation-minimizer' for regex 'libreoffice*'
Note, selecting 'libreoffice-presenter-console' for regex 'libreoffice*'
Note, selecting 'libreoffice-reportdesigner' for regex 'libreoffice*'
Note, selecting 'libreoffice-sdbc-postgresql' for regex 'libreoffice*'
Note, selecting 'libreoffice-wiki-publisher' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer2latex' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer2xhtml' for regex 'libreoffice*'
Note, selecting 'libreoffice-dmaths' for regex 'libreoffice*'
Note, selecting 'libreoffice-zemberek' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-3.3.3' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-3.3.3' for regex 'libreoffice*'
Note, selecting 'libreoffice3.3-mandriva-menus' for regex 'libreoffice*'
Note, selecting 'libreoffice3.3-redhat-menus' for regex 'libreoffice*'
Note, selecting 'libreoffice3.3-suse-menus' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-human' instead of 'libreoffice-style-default'
Note, selecting 'libreoffice-common' instead of 'libreoffice-l10n-en-us'
Note, selecting 'libreoffice-core' instead of 'libreoffice-bundled'
Note, selecting 'openoffice.org-dtd-officedocument1.0' instead of 'libreoffice-dtd-officedocument1.0'
Note, selecting 'libreoffice-gnome' instead of 'libreoffice-gtk-gnome'
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-spellcheck-fi'
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-hyphenation-fi'
Note, selecting 'libreoffice-report-builder' instead of 'libreoffice-reportdesigner'
Note, selecting 'openoffice.org-updatedicts' for regex 'openoffice*'
Note, selecting 'openoffice.org-hunspell' for regex 'openoffice*'
Note, selecting 'openoffice.org-core' for regex 'openoffice*'
Note, selecting 'openoffice.org' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-de-at' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-de-ch' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-de-de' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-en-us' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-eu' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-gl' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-uz' for regex 'openoffice*'
Note, selecting 'openoffice.org-writer' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-af' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-ca' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-de' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-en-us' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-en' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-fr' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-hu' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-it' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-pl' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-ro' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-sh' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-sl' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-sr' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-zu' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-ui' for regex 'openoffice*'
Note, selecting 'libbase-java-openoffice.org' for regex 'openoffice*'
Note, selecting 'libflute-java-openoffice.org' for regex 'openoffice*'
Note, selecting 'libfonts-java-openoffice.org' for regex 'openoffice*'
Note, selecting 'libloader-java-openoffice.org' for regex 'openoffice*'
Note, selecting 'libformula-java-openoffice.org' for regex 'openoffice*'
Note, selecting 'openoffice.org-base' for regex 'openoffice*'
Note, selecting 'liblayout-java-openoffice.org' for regex 'openoffice*'
Note, selecting 'librepository-java-openoffice.org' for regex 'openoffice*'
Note, selecting 'libxml-java-openoffice.org' for regex 'openoffice*'
Note, selecting 'libpentaho-reporting-flow-engine-java-openoffice.org' for regex 'openoffice*'
Note, selecting 'libserializer-java-openoffice.org' for regex 'openoffice*'
Note, selecting 'openoffice.org-common' for regex 'openoffice*'
Note, selecting 'openoffice.org-dev-doc' for regex 'openoffice*'
Note, selecting 'openoffice.org-kde' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-ca' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-eo' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-es' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-et' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-et' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-fo' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-fr-fr' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-lv' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-lv' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-nb' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-nn' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-nr' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-ns' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-ru' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-ss' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-st' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-tn' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-ve' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-xh' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-zu' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-ca' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-cs' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-de' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-de-ch' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-en-us' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-fr' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-hu' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-ne' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-pl' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-ro' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-ru' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-sk' for regex 'openoffice*'
Note, selecting 'openoffice.org-calc' for regex 'openoffice*'
Note, selecting 'openoffice.org-gcj' for regex 'openoffice*'
Note, selecting 'openoffice.org-gnome' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-ca' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-cs' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-da' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-de' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-dz' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-el' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-en-gb' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-en-us' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-es' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-et' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-eu' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-fi' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-fr' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-gl' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-hi-in' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-hu' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-it' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-ja' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-km' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-ko' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-nl' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-om' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-pl' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-pt' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-pt-br' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-ru' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-sl' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-sv' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-zh-cn' for regex 'openoffice*'
Note, selecting 'openoffice.org-help-zh-tw' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-cs' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-da' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-el' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-es' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-fi' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-ga' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-id' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-is' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-nl' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-pt' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-ru' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-sk' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-sv' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-uk' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-hr' for regex 'openoffice*'
Note, selecting 'openoffice.org-impress' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-lt' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-af' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ar' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-as' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ast' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-be-by' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-bg' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-bn' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-br' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-bs' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ca' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-cs' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-cy' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-da' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-de' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-dz' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-el' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-en-gb' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-en-za' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-eo' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-es' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-et' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-eu' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-fa' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-fi' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-fr' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ga' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-gl' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-gu' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-he' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-hi-in' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-hr' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-hu' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-id' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-in' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-it' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ja' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ka' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-km' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ko' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ku' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-lt' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-lv' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-mk' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ml' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-mn' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-mr' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-nb' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ne' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-nl' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-nn' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-nr' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ns' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-oc' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-om' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-or' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-pa-in' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-pl' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-pt' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-pt-br' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ro' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ru' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-rw' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-si' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-sk' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-sl' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-sr' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ss' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-st' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-sv' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ta' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-te' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-tg' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-th' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-tn' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-tr' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ts' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ug' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-uk' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-uz' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-ve' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-vi' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-xh' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-za' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-zh-cn' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-zh-tw' for regex 'openoffice*'
Note, selecting 'openoffice.org-l10n-zu' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-en-au' for regex 'openoffice*'
Note, selecting 'openoffice.org2-thesaurus' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-it' for regex 'openoffice*'
Note, selecting 'openoffice.org2-thesaurus-it' for regex 'openoffice*'
Note, selecting 'openoffice.org-voikko' for regex 'openoffice*'
Note, selecting 'libopenoffice-oodoc-perl' for regex 'openoffice*'
Note, selecting 'openoffice.org-gtk' for regex 'openoffice*'
Note, selecting 'docvert-openoffice.org' for regex 'openoffice*'
Note, selecting 'openoffice.org-draw' for regex 'openoffice*'
Note, selecting 'openoffice.org-evolution' for regex 'openoffice*'
Note, selecting 'ia32-libs-openoffice.org' for regex 'openoffice*'
Note, selecting 'openoffice.org-java-common' for regex 'openoffice*'
Note, selecting 'kde-thumbnailer-openoffice' for regex 'openoffice*'
Note, selecting 'libming-fonts-openoffice' for regex 'openoffice*'
Note, selecting 'mozilla-openoffice.org' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-fi' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-tl' for regex 'openoffice*'
Note, selecting 'openclipart-openoffice.org' for regex 'openoffice*'
Note, selecting 'openoffice.org-dmaths' for regex 'openoffice*'
Note, selecting 'openoffice.org-mysql-connector' for regex 'openoffice*'
Note, selecting 'openoffice.org-presentation-minimizer' for regex 'openoffice*'
Note, selecting 'openoffice.org-presenter-console' for regex 'openoffice*'
Note, selecting 'openoffice.org-report-builder' for regex 'openoffice*'
Note, selecting 'openoffice.org-sdbc-postgresql' for regex 'openoffice*'
Note, selecting 'openoffice.org-wiki-publisher' for regex 'openoffice*'
Note, selecting 'openoffice.org-coooder' for regex 'openoffice*'
Note, selecting 'openoffice.org-ctl-he' for regex 'openoffice*'
Note, selecting 'openoffice.org-dtd-officedocument1.0' for regex 'openoffice*'
Note, selecting 'openoffice.org-emailmerge' for regex 'openoffice*'
Note, selecting 'openoffice.org-filter-binfilter' for regex 'openoffice*'
Note, selecting 'openoffice.org-filter-mobiledev' for regex 'openoffice*'
Note, selecting 'openoffice.org-math' for regex 'openoffice*'
Note, selecting 'openoffice.org-officebean' for regex 'openoffice*'
Note, selecting 'openoffice.org-ogltrans' for regex 'openoffice*'
Note, selecting 'openoffice.org-pdfimport' for regex 'openoffice*'
Note, selecting 'openoffice.org-starter-guide' for regex 'openoffice*'
Note, selecting 'openoffice.org-style-andromeda' for regex 'openoffice*'
Note, selecting 'openoffice.org-style-crystal' for regex 'openoffice*'
Note, selecting 'openoffice.org-style-galaxy' for regex 'openoffice*'
Note, selecting 'openoffice.org-style-hicontrast' for regex 'openoffice*'
Note, selecting 'openoffice.org-style-oxygen' for regex 'openoffice*'
Note, selecting 'openoffice.org-style-tango' for regex 'openoffice*'
Note, selecting 'openoffice.org-writer2latex' for regex 'openoffice*'
Note, selecting 'openoffice.org-writer2xhtml' for regex 'openoffice*'
Note, selecting 'openoffice.org-zemberek' for regex 'openoffice*'
Note, selecting 'python-openoffice' for regex 'openoffice*'
Note, selecting 'openoffice.org-headless' for regex 'openoffice*'
Note, selecting 'openoffice-ctl-he' for regex 'openoffice*'
Note, selecting 'dictionaries-common' instead of 'openoffice.org-updatedicts'
Note, selecting 'hunspell-eu-es' instead of 'openoffice.org-spellcheck-eu'
Note, selecting 'hunspell-gl-es' instead of 'openoffice.org-spellcheck-gl'
Note, selecting 'hunspell-uz' instead of 'openoffice.org-spellcheck-uz'
Note, selecting 'hyphen-pl' instead of 'openoffice.org-hyphenation-pl'
Note, selecting 'hyphen-zu' instead of 'openoffice.org-hyphenation-ui'
Note, selecting 'myspell-ca' instead of 'openoffice.org-spellcheck-ca'
Note, selecting 'myspell-eo' instead of 'openoffice.org-spellcheck-eo'
Note, selecting 'myspell-es' instead of 'openoffice.org-spellcheck-es'
Note, selecting 'myspell-et' instead of 'openoffice.org-hyphenation-et'
Note, selecting 'myspell-et' instead of 'openoffice.org-spellcheck-et'
Note, selecting 'myspell-fo' instead of 'openoffice.org-spellcheck-fo'
Note, selecting 'myspell-fr-gut' instead of 'openoffice.org-spellcheck-fr-fr'
Note, selecting 'myspell-lv' instead of 'openoffice.org-hyphenation-lv'
Note, selecting 'myspell-lv' instead of 'openoffice.org-spellcheck-lv'
Note, selecting 'myspell-nb' instead of 'openoffice.org-spellcheck-nb'
Note, selecting 'myspell-nn' instead of 'openoffice.org-spellcheck-nn'
Note, selecting 'myspell-nr' instead of 'openoffice.org-spellcheck-nr'
Note, selecting 'myspell-ns' instead of 'openoffice.org-spellcheck-ns'
Note, selecting 'myspell-ru' instead of 'openoffice.org-spellcheck-ru'
Note, selecting 'myspell-ss' instead of 'openoffice.org-spellcheck-ss'
Note, selecting 'myspell-st' instead of 'openoffice.org-spellcheck-st'
Note, selecting 'myspell-tn' instead of 'openoffice.org-spellcheck-tn'
Note, selecting 'myspell-ve' instead of 'openoffice.org-spellcheck-ve'
Note, selecting 'myspell-xh' instead of 'openoffice.org-spellcheck-xh'
Note, selecting 'myspell-zu' instead of 'openoffice.org-spellcheck-zu'
Note, selecting 'mythes-pl' instead of 'openoffice.org-thesaurus-pl'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-cs'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-da'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-el'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-es'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-fi'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-ga'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-id'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-is'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-nl'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-pt'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-ru'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-sk'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-sv'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-uk'
Note, selecting 'openoffice.org-thesaurus-it' instead of 'openoffice.org2-thesaurus-it'
Note, selecting 'ming-fonts-opensymbol' instead of 'libming-fonts-openoffice'
Note, selecting 'myspell-fi' instead of 'openoffice.org-spellcheck-fi'
Note, selecting 'myspell-tl' instead of 'openoffice.org-spellcheck-tl'
Package dictionaries-common is not installed, so not removed
Package hunspell-eu-es is not installed, so not removed
Package hunspell-gl-es is not installed, so not removed
Package hunspell-uz is not installed, so not removed
Package hyphen-pl is not installed, so not removed
Package hyphen-zu is not installed, so not removed
Package libbase-java-openoffice.org is not installed, so not removed
Package libflute-java-openoffice.org is not installed, so not removed
Package libfonts-java-openoffice.org is not installed, so not removed
Package libformula-java-openoffice.org is not installed, so not removed
Package liblayout-java-openoffice.org is not installed, so not removed
Package libloader-java-openoffice.org is not installed, so not removed
Package libpentaho-reporting-flow-engine-java-openoffice.org is not installed, so not removed
Package libreoffice-nlpsolver is not installed, so not removed
Package libreoffice-voikko is not installed, so not removed
Package librepository-java-openoffice.org is not installed, so not removed
Package libserializer-java-openoffice.org is not installed, so not removed
Package libxml-java-openoffice.org is not installed, so not removed
Package myspell-ca is not installed, so not removed
Package myspell-eo is not installed, so not removed
Package myspell-es is not installed, so not removed
Package myspell-et is not installed, so not removed
Package myspell-fo is not installed, so not removed
Package myspell-lv is not installed, so not removed
Package myspell-nb is not installed, so not removed
Package myspell-nn is not installed, so not removed
Package myspell-nr is not installed, so not removed
Package myspell-ns is not installed, so not removed
Package myspell-ru is not installed, so not removed
Package myspell-ss is not installed, so not removed
Package myspell-st is not installed, so not removed
Package myspell-tn is not installed, so not removed
Package myspell-ve is not installed, so not removed
Package myspell-xh is not installed, so not removed
Package myspell-zu is not installed, so not removed
Package mythes-pl is not installed, so not removed
Package openoffice.org-hyphenation is not installed, so not removed
Package openoffice.org-hyphenation-hr is not installed, so not removed
Package openoffice.org-hyphenation-lt is not installed, so not removed
Package openoffice.org-thesaurus-en-au is not installed, so not removed
Package openoffice.org-thesaurus-it is not installed, so not removed
Package docvert-libreoffice is not installed, so not removed
Package kde-thumbnailer-openoffice is not installed, so not removed
Package libopenoffice-oodoc-perl is not installed, so not removed
Package libreoffice-writer2latex is not installed, so not removed
Package libreoffice-writer2xhtml is not installed, so not removed
Package ming-fonts-opensymbol is not installed, so not removed
Package myspell-fi is not installed, so not removed
Package myspell-fr-gut is not installed, so not removed
Package myspell-tl is not installed, so not removed
Package openoffice.org-coooder is not installed, so not removed
Package openoffice.org-ctl-he is not installed, so not removed
Package openoffice.org-starter-guide is not installed, so not removed
Package python-openoffice is not installed, so not removed
Package libreoffice-base is not installed, so not removed
Package libreoffice-base-core is not installed, so not removed
Package libreoffice-calc is not installed, so not removed
Package libreoffice-common is not installed, so not removed
Package libreoffice-core is not installed, so not removed
Package libreoffice-dbg is not installed, so not removed
Package libreoffice-dev is not installed, so not removed
Package libreoffice-dev-doc is not installed, so not removed
Package libreoffice-draw is not installed, so not removed
Package libreoffice-emailmerge is not installed, so not removed
Package libreoffice-filter-binfilter is not installed, so not removed
Package libreoffice-gcj is not installed, so not removed
Package libreoffice-gnome is not installed, so not removed
Package libreoffice-gtk is not installed, so not removed
Package libreoffice-help-ca is not installed, so not removed
Package libreoffice-help-cs is not installed, so not removed
Package libreoffice-help-da is not installed, so not removed
Package libreoffice-help-de is not installed, so not removed
Package libreoffice-help-dz is not installed, so not removed
Package libreoffice-help-el is not installed, so not removed
Package libreoffice-help-en-gb is not installed, so not removed
Package libreoffice-help-en-us is not installed, so not removed
Package libreoffice-help-es is not installed, so not removed
Package libreoffice-help-et is not installed, so not removed
Package libreoffice-help-eu is not installed, so not removed
Package libreoffice-help-fi is not installed, so not removed
Package libreoffice-help-fr is not installed, so not removed
Package libreoffice-help-gl is not installed, so not removed
Package libreoffice-help-hi is not installed, so not removed
Package libreoffice-help-hu is not installed, so not removed
Package libreoffice-help-it is not installed, so not removed
Package libreoffice-help-ja is not installed, so not removed
Package libreoffice-help-km is not installed, so not removed
Package libreoffice-help-ko is not installed, so not removed
Package libreoffice-help-nl is not installed, so not removed
Package libreoffice-help-om is not installed, so not removed
Package libreoffice-help-pl is not installed, so not removed
Package libreoffice-help-pt is not installed, so not removed
Package libreoffice-help-pt-br is not installed, so not removed
Package libreoffice-help-ru is not installed, so not removed
Package libreoffice-help-sk is not installed, so not removed
Package libreoffice-help-sl is not installed, so not removed
Package libreoffice-help-sv is not installed, so not removed
Package libreoffice-help-zh-cn is not installed, so not removed
Package libreoffice-help-zh-tw is not installed, so not removed
Package libreoffice-impress is not installed, so not removed
Package libreoffice-java-common is not installed, so not removed
Package libreoffice-kde is not installed, so not removed
Package libreoffice-l10n-af is not installed, so not removed
Package libreoffice-l10n-ar is not installed, so not removed
Package libreoffice-l10n-as is not installed, so not removed
Package libreoffice-l10n-ast is not installed, so not removed
Package libreoffice-l10n-be-by is not installed, so not removed
Package libreoffice-l10n-bg is not installed, so not removed
Package libreoffice-l10n-bn is not installed, so not removed
Package libreoffice-l10n-br is not installed, so not removed
Package libreoffice-l10n-bs is not installed, so not removed
Package libreoffice-l10n-ca is not installed, so not removed
Package libreoffice-l10n-common is not installed, so not removed
Package libreoffice-l10n-cs is not installed, so not removed
Package libreoffice-l10n-cy is not installed, so not removed
Package libreoffice-l10n-da is not installed, so not removed
Package libreoffice-l10n-de is not installed, so not removed
Package libreoffice-l10n-dz is not installed, so not removed
Package libreoffice-l10n-el is not installed, so not removed
Package libreoffice-l10n-en-gb is not installed, so not removed
Package libreoffice-l10n-en-za is not installed, so not removed
Package libreoffice-l10n-eo is not installed, so not removed
Package libreoffice-l10n-es is not installed, so not removed
Package libreoffice-l10n-et is not installed, so not removed
Package libreoffice-l10n-eu is not installed, so not removed
Package libreoffice-l10n-fa is not installed, so not removed
Package libreoffice-l10n-fi is not installed, so not removed
Package libreoffice-l10n-fr is not installed, so not removed
Package libreoffice-l10n-ga is not installed, so not removed
Package libreoffice-l10n-gl is not installed, so not removed
Package libreoffice-l10n-gu is not installed, so not removed
Package libreoffice-l10n-he is not installed, so not removed
Package libreoffice-l10n-hi is not installed, so not removed
Package libreoffice-l10n-hr is not installed, so not removed
Package libreoffice-l10n-hu is not installed, so not removed
Package libreoffice-l10n-id is not installed, so not removed
Package libreoffice-l10n-in is not installed, so not removed
Package libreoffice-l10n-is is not installed, so not removed
Package libreoffice-l10n-it is not installed, so not removed
Package libreoffice-l10n-ja is not installed, so not removed
Package libreoffice-l10n-ka is not installed, so not removed
Package libreoffice-l10n-km is not installed, so not removed
Package libreoffice-l10n-ko is not installed, so not removed
Package libreoffice-l10n-ku is not installed, so not removed
Package libreoffice-l10n-lt is not installed, so not removed
Package libreoffice-l10n-lv is not installed, so not removed
Package libreoffice-l10n-mk is not installed, so not removed
Package libreoffice-l10n-ml is not installed, so not removed
Package libreoffice-l10n-mn is not installed, so not removed
Package libreoffice-l10n-mr is not installed, so not removed
Package libreoffice-l10n-nb is not installed, so not removed
Package libreoffice-l10n-ne is not installed, so not removed
Package libreoffice-l10n-nl is not installed, so not removed
Package libreoffice-l10n-nn is not installed, so not removed
Package libreoffice-l10n-nr is not installed, so not removed
Package libreoffice-l10n-ns is not installed, so not removed
Package libreoffice-l10n-oc is not installed, so not removed
Package libreoffice-l10n-om is not installed, so not removed
Package libreoffice-l10n-or is not installed, so not removed
Package libreoffice-l10n-pa-in is not installed, so not removed
Package libreoffice-l10n-pl is not installed, so not removed
Package libreoffice-l10n-pt is not installed, so not removed
Package libreoffice-l10n-pt-br is not installed, so not removed
Package libreoffice-l10n-ro is not installed, so not removed
Package libreoffice-l10n-ru is not installed, so not removed
Package libreoffice-l10n-rw is not installed, so not removed
Package libreoffice-l10n-si is not installed, so not removed
Package libreoffice-l10n-sk is not installed, so not removed
Package libreoffice-l10n-sl is not installed, so not removed
Package libreoffice-l10n-sr is not installed, so not removed
Package libreoffice-l10n-ss is not installed, so not removed
Package libreoffice-l10n-st is not installed, so not removed
Package libreoffice-l10n-sv is not installed, so not removed
Package libreoffice-l10n-ta is not installed, so not removed
Package libreoffice-l10n-te is not installed, so not removed
Package libreoffice-l10n-tg is not installed, so not removed
Package libreoffice-l10n-th is not installed, so not removed
Package libreoffice-l10n-tn is not installed, so not removed
Package libreoffice-l10n-tr is not installed, so not removed
Package libreoffice-l10n-ts is not installed, so not removed
Package libreoffice-l10n-ug is not installed, so not removed
Package libreoffice-l10n-uk is not installed, so not removed
Package libreoffice-l10n-uz is not installed, so not removed
Package libreoffice-l10n-ve is not installed, so not removed
Package libreoffice-l10n-vi is not installed, so not removed
Package libreoffice-l10n-xh is not installed, so not removed
Package libreoffice-l10n-za is not installed, so not removed
Package libreoffice-l10n-zh-cn is not installed, so not removed
Package libreoffice-l10n-zh-tw is not installed, so not removed
Package libreoffice-l10n-zu is not installed, so not removed
Package libreoffice-math is not installed, so not removed
Package libreoffice-officebean is not installed, so not removed
Package libreoffice-style-andromeda is not installed, so not removed
Package libreoffice-style-human is not installed, so not removed
Package libreoffice-style-oxygen is not installed, so not removed
Package libreoffice-style-tango is not installed, so not removed
Package libreoffice-writer is not installed, so not removed
Package openoffice.org-base is not installed, so not removed
Package openoffice.org-calc is not installed, so not removed
Package openoffice.org-gcj is not installed, so not removed
Package openoffice.org-gnome is not installed, so not removed
Package openoffice.org-help-ca is not installed, so not removed
Package openoffice.org-help-cs is not installed, so not removed
Package openoffice.org-help-da is not installed, so not removed
Package openoffice.org-help-de is not installed, so not removed
Package openoffice.org-help-dz is not installed, so not removed
Package openoffice.org-help-el is not installed, so not removed
Package openoffice.org-help-en-gb is not installed, so not removed
Package openoffice.org-help-en-us is not installed, so not removed
Package openoffice.org-help-es is not installed, so not removed
Package openoffice.org-help-et is not installed, so not removed
Package openoffice.org-help-eu is not installed, so not removed
Package openoffice.org-help-fi is not installed, so not removed
Package openoffice.org-help-fr is not installed, so not removed
Package openoffice.org-help-gl is not installed, so not removed
Package openoffice.org-help-hi-in is not installed, so not removed
Package openoffice.org-help-hu is not installed, so not removed
Package openoffice.org-help-it is not installed, so not removed
Package openoffice.org-help-ja is not installed, so not removed
Package openoffice.org-help-km is not installed, so not removed
Package openoffice.org-help-ko is not installed, so not removed
Package openoffice.org-help-nl is not installed, so not removed
Package openoffice.org-help-om is not installed, so not removed
Package openoffice.org-help-pl is not installed, so not removed
Package openoffice.org-help-pt is not installed, so not removed
Package openoffice.org-help-pt-br is not installed, so not removed
Package openoffice.org-help-ru is not installed, so not removed
Package openoffice.org-help-sl is not installed, so not removed
Package openoffice.org-help-sv is not installed, so not removed
Package openoffice.org-help-zh-cn is not installed, so not removed
Package openoffice.org-help-zh-tw is not installed, so not removed
Package openoffice.org-hyphenation-af is not installed, so not removed
Package openoffice.org-hyphenation-ca is not installed, so not removed
Package openoffice.org-hyphenation-de is not installed, so not removed
Package openoffice.org-hyphenation-en-us is not installed, so not removed
Package openoffice.org-hyphenation-fr is not installed, so not removed
Package openoffice.org-hyphenation-hu is not installed, so not removed
Package openoffice.org-hyphenation-it is not installed, so not removed
Package openoffice.org-hyphenation-ro is not installed, so not removed
Package openoffice.org-hyphenation-sh is not installed, so not removed
Package openoffice.org-hyphenation-sl is not installed, so not removed
Package openoffice.org-hyphenation-sr is not installed, so not removed
Package openoffice.org-hyphenation-zu is not installed, so not removed
Package openoffice.org-impress is not installed, so not removed
Package openoffice.org-l10n-af is not installed, so not removed
Package openoffice.org-l10n-ar is not installed, so not removed
Package openoffice.org-l10n-as is not installed, so not removed
Package openoffice.org-l10n-ast is not installed, so not removed
Package openoffice.org-l10n-be-by is not installed, so not removed
Package openoffice.org-l10n-bg is not installed, so not removed
Package openoffice.org-l10n-bn is not installed, so not removed
Package openoffice.org-l10n-br is not installed, so not removed
Package openoffice.org-l10n-bs is not installed, so not removed
Package openoffice.org-l10n-ca is not installed, so not removed
Package openoffice.org-l10n-cs is not installed, so not removed
Package openoffice.org-l10n-cy is not installed, so not removed
Package openoffice.org-l10n-da is not installed, so not removed
Package openoffice.org-l10n-de is not installed, so not removed
Package openoffice.org-l10n-dz is not installed, so not removed
Package openoffice.org-l10n-el is not installed, so not removed
Package openoffice.org-l10n-en-gb is not installed, so not removed
Package openoffice.org-l10n-en-za is not installed, so not removed
Package openoffice.org-l10n-eo is not installed, so not removed
Package openoffice.org-l10n-es is not installed, so not removed
Package openoffice.org-l10n-et is not installed, so not removed
Package openoffice.org-l10n-eu is not installed, so not removed
Package openoffice.org-l10n-fa is not installed, so not removed
Package openoffice.org-l10n-fi is not installed, so not removed
Package openoffice.org-l10n-fr is not installed, so not removed
Package openoffice.org-l10n-ga is not installed, so not removed
Package openoffice.org-l10n-gl is not installed, so not removed
Package openoffice.org-l10n-gu is not installed, so not removed
Package openoffice.org-l10n-he is not installed, so not removed
Package openoffice.org-l10n-hi-in is not installed, so not removed
Package openoffice.org-l10n-hr is not installed, so not removed
Package openoffice.org-l10n-hu is not installed, so not removed
Package openoffice.org-l10n-id is not installed, so not removed
Package openoffice.org-l10n-in is not installed, so not removed
Package openoffice.org-l10n-it is not installed, so not removed
Package openoffice.org-l10n-ja is not installed, so not removed
Package openoffice.org-l10n-ka is not installed, so not removed
Package openoffice.org-l10n-km is not installed, so not removed
Package openoffice.org-l10n-ko is not installed, so not removed
Package openoffice.org-l10n-ku is not installed, so not removed
Package openoffice.org-l10n-lt is not installed, so not removed
Package openoffice.org-l10n-lv is not installed, so not removed
Package openoffice.org-l10n-mk is not installed, so not removed
Package openoffice.org-l10n-ml is not installed, so not removed
Package openoffice.org-l10n-mn is not installed, so not removed
Package openoffice.org-l10n-mr is not installed, so not removed
Package openoffice.org-l10n-nb is not installed, so not removed
Package openoffice.org-l10n-ne is not installed, so not removed
Package openoffice.org-l10n-nl is not installed, so not removed
Package openoffice.org-l10n-nn is not installed, so not removed
Package openoffice.org-l10n-nr is not installed, so not removed
Package openoffice.org-l10n-ns is not installed, so not removed
Package openoffice.org-l10n-oc is not installed, so not removed
Package openoffice.org-l10n-om is not installed, so not removed
Package openoffice.org-l10n-or is not installed, so not removed
Package openoffice.org-l10n-pa-in is not installed, so not removed
Package openoffice.org-l10n-pl is not installed, so not removed
Package openoffice.org-l10n-pt is not installed, so not removed
Package openoffice.org-l10n-pt-br is not installed, so not removed
Package openoffice.org-l10n-ro is not installed, so not removed
Package openoffice.org-l10n-ru is not installed, so not removed
Package openoffice.org-l10n-rw is not installed, so not removed
Package openoffice.org-l10n-si is not installed, so not removed
Package openoffice.org-l10n-sk is not installed, so not removed
Package openoffice.org-l10n-sl is not installed, so not removed
Package openoffice.org-l10n-sr is not installed, so not removed
Package openoffice.org-l10n-ss is not installed, so not removed
Package openoffice.org-l10n-st is not installed, so not removed
Package openoffice.org-l10n-sv is not installed, so not removed
Package openoffice.org-l10n-ta is not installed, so not removed
Package openoffice.org-l10n-te is not installed, so not removed
Package openoffice.org-l10n-tg is not installed, so not removed
Package openoffice.org-l10n-th is not installed, so not removed
Package openoffice.org-l10n-tn is not installed, so not removed
Package openoffice.org-l10n-tr is not installed, so not removed
Package openoffice.org-l10n-ts is not installed, so not removed
Package openoffice.org-l10n-ug is not installed, so not removed
Package openoffice.org-l10n-uk is not installed, so not removed
Package openoffice.org-l10n-uz is not installed, so not removed
Package openoffice.org-l10n-ve is not installed, so not removed
Package openoffice.org-l10n-vi is not installed, so not removed
Package openoffice.org-l10n-xh is not installed, so not removed
Package openoffice.org-l10n-za is not installed, so not removed
Package openoffice.org-l10n-zh-cn is not installed, so not removed
Package openoffice.org-l10n-zh-tw is not installed, so not removed
Package openoffice.org-l10n-zu is not installed, so not removed
Package openoffice.org-thesaurus-ca is not installed, so not removed
Package openoffice.org-thesaurus-cs is not installed, so not removed
Package openoffice.org-thesaurus-de is not installed, so not removed
Package openoffice.org-thesaurus-de-ch is not installed, so not removed
Package openoffice.org-thesaurus-en-us is not installed, so not removed
Package openoffice.org-thesaurus-fr is not installed, so not removed
Package openoffice.org-thesaurus-hu is not installed, so not removed
Package openoffice.org-thesaurus-ne is not installed, so not removed
Package openoffice.org-thesaurus-ro is not installed, so not removed
Package openoffice.org-thesaurus-ru is not installed, so not removed
Package openoffice.org-thesaurus-sk is not installed, so not removed
Package openoffice.org-voikko is not installed, so not removed
Package openoffice.org-writer is not installed, so not removed
Package docvert-openoffice.org is not installed, so not removed
Package libreoffice is not installed, so not removed
Package libreoffice-evolution is not installed, so not removed
Package libreoffice-filter-mobiledev is not installed, so not removed
Package libreoffice-mysql-connector is not installed, so not removed
Package libreoffice-ogltrans is not installed, so not removed
Package libreoffice-pdfimport is not installed, so not removed
Package libreoffice-presentation-minimizer is not installed, so not removed
Package libreoffice-presenter-console is not installed, so not removed
Package libreoffice-report-builder is not installed, so not removed
Package libreoffice-report-builder-bin is not installed, so not removed
Package libreoffice-sdbc-postgresql is not installed, so not removed
Package libreoffice-style-crystal is not installed, so not removed
Package libreoffice-style-galaxy is not installed, so not removed
Package libreoffice-style-hicontrast is not installed, so not removed
Package libreoffice-wiki-publisher is not installed, so not removed
Package mozilla-libreoffice is not installed, so not removed
Package mozilla-openoffice.org is not installed, so not removed
Package openclipart-libreoffice is not installed, so not removed
Package openclipart-openoffice.org is not installed, so not removed
Package openoffice.org is not installed, so not removed
Package openoffice.org-common is not installed, so not removed
Package openoffice.org-dmaths is not installed, so not removed
Package openoffice.org-draw is not installed, so not removed
Package openoffice.org-dtd-officedocument1.0 is not installed, so not removed
Package openoffice.org-emailmerge is not installed, so not removed
Package openoffice.org-filter-binfilter is not installed, so not removed
Package openoffice.org-filter-mobiledev is not installed, so not removed
Package openoffice.org-gtk is not installed, so not removed
Package openoffice.org-java-common is not installed, so not removed
Package openoffice.org-kde is not installed, so not removed
Package openoffice.org-math is not installed, so not removed
Package openoffice.org-mysql-connector is not installed, so not removed
Package openoffice.org-officebean is not installed, so not removed
Package openoffice.org-ogltrans is not installed, so not removed
Package openoffice.org-pdfimport is not installed, so not removed
Package openoffice.org-presentation-minimizer is not installed, so not removed
Package openoffice.org-presenter-console is not installed, so not removed
Package openoffice.org-report-builder is not installed, so not removed
Package openoffice.org-sdbc-postgresql is not installed, so not removed
Package openoffice.org-style-andromeda is not installed, so not removed
Package openoffice.org-style-crystal is not installed, so not removed
Package openoffice.org-style-galaxy is not installed, so not removed
Package openoffice.org-style-hicontrast is not installed, so not removed
Package openoffice.org-style-oxygen is not installed, so not removed
Package openoffice.org-style-tango is not installed, so not removed
Package openoffice.org-wiki-publisher is not installed, so not removed
Package openoffice.org-writer2latex is not installed, so not removed
Package openoffice.org-writer2xhtml is not installed, so not removed
Package openoffice.org-zemberek is not installed, so not removed
The following packages were automatically installed and are no longer required:
  ttf-dejavu-extra ttf-sil-gentium libhsqldb-java libgif4 libservlet2.5-java ttf-sil-gentium-basic ttf-dejavu
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
florian@system:~$ clear

florian@system:~$ cd Downloads/
florian@system:~/Downloads$ ls
LibO_3.3.4rc1_Linux_x86-64_helppack-deb_en-US         LibO_3.3.4rc1_Linux_x86-64_install-deb_en-US
LibO_3.3.4rc1_Linux_x86-64_helppack-deb_en-US.tar.gz  LibO_3.3.4rc1_Linux_x86-64_install-deb_en-US.tar.gz
florian@system:~/Downloads$ cd LibO_3.3.4rc1_Linux_x86-64_install-deb_en-US/DEBS/
florian@system:~/Downloads/LibO_3.3.4rc1_Linux_x86-64_install-deb_en-US/DEBS$ sudo dpkg -i *.deb
Selecting previously deselected package libobasis3.3-base.
(Reading database ... 184811 files and directories currently installed.)
Unpacking libobasis3.3-base (from libobasis3.3-base_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-binfilter.
Unpacking libobasis3.3-binfilter (from libobasis3.3-binfilter_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-calc.
Unpacking libobasis3.3-calc (from libobasis3.3-calc_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-core01.
Unpacking libobasis3.3-core01 (from libobasis3.3-core01_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-core02.
Unpacking libobasis3.3-core02 (from libobasis3.3-core02_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-core03.
Unpacking libobasis3.3-core03 (from libobasis3.3-core03_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-core04.
Unpacking libobasis3.3-core04 (from libobasis3.3-core04_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-core05.
Unpacking libobasis3.3-core05 (from libobasis3.3-core05_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-core06.
Unpacking libobasis3.3-core06 (from libobasis3.3-core06_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-core07.
Unpacking libobasis3.3-core07 (from libobasis3.3-core07_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-draw.
Unpacking libobasis3.3-draw (from libobasis3.3-draw_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-en-us.
Unpacking libobasis3.3-en-us (from libobasis3.3-en-us_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-en-us-base.
Unpacking libobasis3.3-en-us-base (from libobasis3.3-en-us-base_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-en-us-binfilter.
Unpacking libobasis3.3-en-us-binfilter (from libobasis3.3-en-us-binfilter_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-en-us-calc.
Unpacking libobasis3.3-en-us-calc (from libobasis3.3-en-us-calc_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-en-us-math.
Unpacking libobasis3.3-en-us-math (from libobasis3.3-en-us-math_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-en-us-res.
Unpacking libobasis3.3-en-us-res (from libobasis3.3-en-us-res_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-en-us-writer.
Unpacking libobasis3.3-en-us-writer (from libobasis3.3-en-us-writer_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-extension-mediawiki-publisher.
Unpacking libobasis3.3-extension-mediawiki-publisher (from libobasis3.3-extension-mediawiki-publisher_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-extension-nlpsolver.
Unpacking libobasis3.3-extension-nlpsolver (from libobasis3.3-extension-nlpsolver_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-extension-pdf-import.
Unpacking libobasis3.3-extension-pdf-import (from libobasis3.3-extension-pdf-import_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-extension-presentation-minimizer.
Unpacking libobasis3.3-extension-presentation-minimizer (from libobasis3.3-extension-presentation-minimizer_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-extension-presenter-screen.
Unpacking libobasis3.3-extension-presenter-screen (from libobasis3.3-extension-presenter-screen_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-extension-report-builder.
Unpacking libobasis3.3-extension-report-builder (from libobasis3.3-extension-report-builder_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-gnome-integration.
Unpacking libobasis3.3-gnome-integration (from libobasis3.3-gnome-integration_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-graphicfilter.
Unpacking libobasis3.3-graphicfilter (from libobasis3.3-graphicfilter_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-images.
Unpacking libobasis3.3-images (from libobasis3.3-images_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-impress.
Unpacking libobasis3.3-impress (from libobasis3.3-impress_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-javafilter.
Unpacking libobasis3.3-javafilter (from libobasis3.3-javafilter_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-kde-integration.
Unpacking libobasis3.3-kde-integration (from libobasis3.3-kde-integration_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-math.
Unpacking libobasis3.3-math (from libobasis3.3-math_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-ogltrans.
Unpacking libobasis3.3-ogltrans (from libobasis3.3-ogltrans_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-ooofonts.
Unpacking libobasis3.3-ooofonts (from libobasis3.3-ooofonts_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-ooolinguistic.
Unpacking libobasis3.3-ooolinguistic (from libobasis3.3-ooolinguistic_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-pyuno.
Unpacking libobasis3.3-pyuno (from libobasis3.3-pyuno_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-testtool.
Unpacking libobasis3.3-testtool (from libobasis3.3-testtool_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-writer.
Unpacking libobasis3.3-writer (from libobasis3.3-writer_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libobasis3.3-xsltfilter.
Unpacking libobasis3.3-xsltfilter (from libobasis3.3-xsltfilter_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libreoffice3.
Unpacking libreoffice3 (from libreoffice3_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libreoffice3-base.
Unpacking libreoffice3-base (from libreoffice3-base_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libreoffice3-calc.
Unpacking libreoffice3-calc (from libreoffice3-calc_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libreoffice3-dict-en.
Unpacking libreoffice3-dict-en (from libreoffice3-dict-en_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libreoffice3-dict-es.
Unpacking libreoffice3-dict-es (from libreoffice3-dict-es_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libreoffice3-dict-fr.
Unpacking libreoffice3-dict-fr (from libreoffice3-dict-fr_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libreoffice3-draw.
Unpacking libreoffice3-draw (from libreoffice3-draw_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libreoffice3-en-us.
Unpacking libreoffice3-en-us (from libreoffice3-en-us_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libreoffice3-impress.
Unpacking libreoffice3-impress (from libreoffice3-impress_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libreoffice3-math.
Unpacking libreoffice3-math (from libreoffice3-math_3.3.4-19_amd64.deb) ...
Selecting previously deselected package libreoffice3-ure.
Unpacking libreoffice3-ure (from libreoffice3-ure_1.7.0-19_amd64.deb) ...
Selecting previously deselected package libreoffice3-writer.
Unpacking libreoffice3-writer (from libreoffice3-writer_3.3.4-19_amd64.deb) ...
Setting up libreoffice3-ure (1.7.0-19) ...
Setting up libobasis3.3-core01 (3.3.4-19) ...
Setting up libobasis3.3-core02 (3.3.4-19) ...
Setting up libobasis3.3-core03 (3.3.4-19) ...
Setting up libobasis3.3-core04 (3.3.4-19) ...
Setting up libobasis3.3-core05 (3.3.4-19) ...
Setting up libobasis3.3-core06 (3.3.4-19) ...
Setting up libobasis3.3-core07 (3.3.4-19) ...
Setting up libobasis3.3-draw (3.3.4-19) ...
Setting up libobasis3.3-en-us (3.3.4-19) ...
Setting up libobasis3.3-en-us-base (3.3.4-19) ...
Setting up libobasis3.3-en-us-binfilter (3.3.4-19) ...
Setting up libobasis3.3-en-us-calc (3.3.4-19) ...
Setting up libobasis3.3-en-us-math (3.3.4-19) ...
Setting up libobasis3.3-en-us-res (3.3.4-19) ...
Setting up libobasis3.3-en-us-writer (3.3.4-19) ...
Setting up libobasis3.3-extension-mediawiki-publisher (3.3.4-19) ...
Setting up libobasis3.3-extension-nlpsolver (3.3.4-19) ...
Setting up libobasis3.3-extension-pdf-import (3.3.4-19) ...
Setting up libobasis3.3-extension-presentation-minimizer (3.3.4-19) ...
Setting up libobasis3.3-extension-presenter-screen (3.3.4-19) ...
Setting up libobasis3.3-extension-report-builder (3.3.4-19) ...
Setting up libobasis3.3-gnome-integration (3.3.4-19) ...
Setting up libobasis3.3-graphicfilter (3.3.4-19) ...
Setting up libobasis3.3-images (3.3.4-19) ...
Setting up libobasis3.3-impress (3.3.4-19) ...
Setting up libobasis3.3-javafilter (3.3.4-19) ...
Setting up libobasis3.3-kde-integration (3.3.4-19) ...
Setting up libobasis3.3-math (3.3.4-19) ...
Setting up libobasis3.3-ogltrans (3.3.4-19) ...
Setting up libobasis3.3-ooofonts (3.3.4-19) ...
Setting up libobasis3.3-ooolinguistic (3.3.4-19) ...
Setting up libobasis3.3-pyuno (3.3.4-19) ...
Setting up libobasis3.3-testtool (3.3.4-19) ...
Setting up libobasis3.3-writer (3.3.4-19) ...
Setting up libobasis3.3-xsltfilter (3.3.4-19) ...
Setting up libreoffice3 (3.3.4-19) ...
Setting up libreoffice3-dict-en (3.3.4-19) ...
Setting up libreoffice3-dict-es (3.3.4-19) ...
Setting up libreoffice3-dict-fr (3.3.4-19) ...
Setting up libreoffice3-draw (3.3.4-19) ...
Setting up libreoffice3-en-us (3.3.4-19) ...
Setting up libreoffice3-impress (3.3.4-19) ...
Setting up libreoffice3-math (3.3.4-19) ...
Setting up libreoffice3-writer (3.3.4-19) ...
Setting up libobasis3.3-base (3.3.4-19) ...
Setting up libobasis3.3-binfilter (3.3.4-19) ...
Setting up libobasis3.3-calc (3.3.4-19) ...
Setting up libreoffice3-base (3.3.4-19) ...
Setting up libreoffice3-calc (3.3.4-19) ...
florian@system:~/Downloads/LibO_3.3.4rc1_Linux_x86-64_install-deb_en-US/DEBS$ cd desktop-integration/
florian@system:~/Downloads/LibO_3.3.4rc1_Linux_x86-64_install-deb_en-US/DEBS/desktop-integration$ sudo dpkg -i *.deb
Selecting previously deselected package libreoffice-debian-menus.
(Reading database ... 191920 files and directories currently installed.)
Unpacking libreoffice-debian-menus (from libreoffice3.3-debian-menus_3.3-401_all.deb) ...
Setting up libreoffice-debian-menus (3.3-401) ...
/usr/bin/gtk-update-icon-cache
gtk-update-icon-cache: Cache file created successfully.
/usr/bin/gtk-update-icon-cache
gtk-update-icon-cache: Cache file created successfully.
Processing triggers for hicolor-icon-theme ...
Processing triggers for gnome-icon-theme ...
Processing triggers for shared-mime-info ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
florian@system:~/Downloads/LibO_3.3.4rc1_Linux_x86-64_install-deb_en-US/DEBS/desktop-integration$ cd
florian@system:~$ libreoffice
florian@system:~$ 

```so now I got another error:

a window appears with the following message

The application cannot be started. A general error occured while accesing your central configuration.

even if I do

```
florian@system:~$ sudo rm -rf ~/.libreoffice/

```

there is no changing

---

### Post by Hagar Delest on 2011-08-18
I don't understand, you seem to have installed the deb packages from the tarball, not from alien. Note that when using alien when OOo didn't provide directly the .deb (some time ago).

If you try with a new user (create a new account), do you get the same error?

---

### Post by flo1805 on 2011-08-18
I tried to install the packages on my own BEFORE I got your link. (yesterday I think) There I used alien.
In my post I tried to do exactly like the way in your link.  (so without alien)

with a new user it works fine

---

### Post by Hagar Delest on 2011-08-18
Well, if it works fine for a new user, try to copy this profile to your home to replace yours.

---

### Post by flo1805 on 2011-08-18
with profile you mean ~/.libreofiice??

---

### Post by Hagar Delest on 2011-08-18
Yes.

---

### Post by flo1805 on 2011-08-18
Ok. I did. No changes...

btw, even if we cannot solve the problem, I'm very thankful, that you try to help me so mutch.

---

### Post by Hagar Delest on 2011-08-18
Well, I'm running out of ideas...

You can try to install OOo to see if it does the same or install LibO 3.4.2 (both can run in parallel if installed with the official packages from their web sites).

Have to go to bed now, I hope to see good news tomorrow...

---

### Post by flo1805 on 2011-08-18
ok..I'll try to fix it somehow and tell ypu, if I got a solution.

Thanks for help.

good night

---

### Post by jdb on 2011-08-18
> **flo1805 said:**
> ok..I'll try to fix it somehow and tell ypu, if I got a solution.

Thanks for help.

good night

From your home directory copy and paste this command

```
find .libreoffice -maxdepth 3 -exec ls -ld {} \;
```

and see if anything belongs to root.

jdb

---

### Post by flo1805 on 2011-08-19
so I did and this is the result..I think nothing belongs to root.

```
florian@system:~$ find .libreoffice -maxdepth 3 -exec ls -ld {} \;
drwxr-xr-x 3 florian florian 4096 2011-08-19 09:03 .libreoffice
drwx------ 3 florian florian 4096 2011-08-19 09:03 .libreoffice/3
drwxr-xr-x 17 florian florian 4096 2011-08-19 09:03 .libreoffice/3/user
drwxr-xr-x 2 florian florian 4096 2011-08-19 09:03 .libreoffice/3/user/store
drwxr-xr-x 2 florian florian 4096 2011-08-19 09:03 .libreoffice/3/user/gallery
drwxr-xr-x 2 florian florian 4096 2011-08-19 09:03 .libreoffice/3/user/wordbook
drwxr-xr-x 2 florian florian 4096 2011-08-19 09:03 .libreoffice/3/user/backup
-rw------- 1 florian florian 1094 2011-08-19 09:03 .libreoffice/3/user/registrymodifications.xcu
drwxr-xr-x 3 florian florian 4096 2011-08-19 09:03 .libreoffice/3/user/database
drwxr-xr-x 4 florian florian 4096 2011-08-19 09:03 .libreoffice/3/user/psprint
drwxr-xr-x 2 florian florian 4096 2011-08-19 09:03 .libreoffice/3/user/template
drwxr-xr-x 3 florian florian 4096 2011-08-19 09:03 .libreoffice/3/user/basic
drwxr-xr-x 3 florian florian 4096 2011-08-19 09:03 .libreoffice/3/user/config
drwxr-xr-x 5 florian florian 4096 2011-08-19 09:03 .libreoffice/3/user/extensions
drwxr-xr-x 2 florian florian 4096 2011-08-19 09:03 .libreoffice/3/user/temp
drwxr-xr-x 3 florian florian 4096 2011-08-19 09:03 .libreoffice/3/user/uno_packages
drwxr-xr-x 2 florian florian 4096 2011-08-19 09:03 .libreoffice/3/user/Scripts
drwxr-xr-x 2 florian florian 4096 2011-08-19 09:03 .libreoffice/3/user/autotext
drwxr-xr-x 2 florian florian 4096 2011-08-19 09:03 .libreoffice/3/user/autocorr
florian@system:~$ 

```

but is it right, that I only have rw rights on .libreoffice/3/user/registrymodifications.xcu ??

---

### Post by Hagar Delest on 2011-08-19
Yes, I've the same for the .xcu file.
But my .libreoffice folder is drwxr-xr-x.

---

### Post by flo1805 on 2011-08-19
mine is the same, isin't it??

drwxr-xr-x 3 florian florian 4096 2011-08-19 09:03 .libreoffice

---

### Post by jdb on 2011-08-19
> **flo1805 said:**
> mine is the same, isin't it??

drwxr-xr-x 3 florian florian 4096 2011-08-19 09:03 .libreoffice
Mine are identical:
```
17:58:14 ~ find .libreoffice -maxdepth 3 -exec ls -ld {} \;
drwxr-xr-x 3 dad dad 4096 2011-04-03 14:39 .libreoffice
drwx------ 3 dad dad 4096 2011-08-19 17:55 .libreoffice/3
drwxr-xr-x 17 dad dad 4096 2011-08-19 17:55 .libreoffice/3/user
drwxr-xr-x 3 dad dad 4096 2011-04-03 14:39 .libreoffice/3/user/basic
drwxr-xr-x 3 dad dad 4096 2011-04-03 14:39 .libreoffice/3/user/uno_packages
drwxr-xr-x 2 dad dad 4096 2011-08-19 17:36 .libreoffice/3/user/backup
drwxr-xr-x 4 dad dad 4096 2011-04-03 14:39 .libreoffice/3/user/psprint
drwxr-xr-x 3 dad dad 4096 2011-04-03 14:39 .libreoffice/3/user/database
drwxr-xr-x 2 dad dad 4096 2011-05-22 15:18 .libreoffice/3/user/store
drwxr-xr-x 2 dad dad 4096 2011-06-21 16:47 .libreoffice/3/user/wordbook
drwxr-xr-x 2 dad dad 4096 2011-04-03 14:39 .libreoffice/3/user/template
drwxr-xr-x 2 dad dad 4096 2011-04-03 14:39 .libreoffice/3/user/Scripts
drwxr-xr-x 5 dad dad 4096 2011-04-03 14:39 .libreoffice/3/user/extensions
drwxr-xr-x 3 dad dad 4096 2011-04-03 14:39 .libreoffice/3/user/config
drwxr-xr-x 2 dad dad 4096 2011-04-03 14:39 .libreoffice/3/user/autotext
drwxr-xr-x 2 dad dad 4096 2011-04-03 14:39 .libreoffice/3/user/temp
-rw------- 1 dad dad 112243 2011-08-19 17:55 .libreoffice/3/user/registrymodifications.xcu
drwxr-xr-x 2 dad dad 4096 2011-07-31 22:58 .libreoffice/3/user/gallery
drwxr-xr-x 2 dad dad 4096 2011-04-03 14:39 .libreoffice/3/user/autocorr

```

I can't imagine whats going on, but I'm still thinking about it.

jdb

---

### Post by Elfy on 2011-08-19
Odd, I'd have almost bet money on "I would also wonder if at some point you've started libreoffice as root with sudo and that's causing the issue"

but t'is linux 

I wonder if a 

sudo apt-get purge libreoffice*
cd
rm -r ~/.libreoffice/


Then a reinstall would do it, though I'd be doing the rm -r ~/.libreoffice/ and trying again.

Thoughts

Edits - lots of the same kicking about - but no assuming that the rm was in the right place - just thinking out loudf here

---

### Post by sanderd17 on 2011-08-20
> **forestpiskie said:**
> Odd, I'd have almost bet money on "I would also wonder if at some point you've started libreoffice as root with sudo and that's causing the issue"

but t'is linux 

I wonder if a 

sudo apt-get purge libreoffice*
cd
rm -r ~/.libreoffice/


Then a reinstall would do it, though I'd be doing the rm -r ~/.libreoffice/ and trying again.

Thoughts

Edits - lots of the same kicking about - but no assuming that the rm was in the right place - just thinking out loudf here

Just a little note about your commands. I just have seen a newbie who lost his home folder because of misreading the command. He putted a space after the ~/, which off course deletes the home folder.

If you just say 

cd
rm -r .libreoffice/

I don't think there is a chance of mistyping that which would cause big problems.

And for the LibreOffice problem, I'm really out of ideas.

---

### Post by flo1805 on 2011-08-20
so now i did the following:

```
sudo rm -rf .libreoffice* && sudo apt-get purge libreoffice* && sudo apt-get install libreoffice*
```here the full code:

```
florian@system:~$  sudo rm -rf .libreoffice* && sudo apt-get purge libreoffice* && sudo apt-get install libreoffice*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libreoffice-writer' for regex 'libreoffice*'
Note, selecting 'libreoffice-calc' for regex 'libreoffice*'
Note, selecting 'libreoffice-impress' for regex 'libreoffice*'
Note, selecting 'libreoffice-kde' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-oxygen' for regex 'libreoffice*'
Note, selecting 'libreoffice-base' for regex 'libreoffice*'
Note, selecting 'libreoffice-core' for regex 'libreoffice*'
Note, selecting 'libreoffice-base-core' for regex 'libreoffice*'
Note, selecting 'libreoffice-java-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-gcj' for regex 'libreoffice*'
Note, selecting 'libreoffice-report-builder' for regex 'libreoffice*'
Note, selecting 'libreoffice-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-default' for regex 'libreoffice*'
Note, selecting 'libreoffice-style' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-hicontrast' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-tango' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-crystal' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-human' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-andromeda' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-galaxy' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-industrial' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-us' for regex 'libreoffice*'
Note, selecting 'libreoffice-dev' for regex 'libreoffice*'
Note, selecting 'libreoffice-draw' for regex 'libreoffice*'
Note, selecting 'libreoffice-evolution' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-so52' for regex 'libreoffice*'
Note, selecting 'libreoffice-gnome' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk' for regex 'libreoffice*'
Note, selecting 'libreoffice-officebean' for regex 'libreoffice*'
Note, selecting 'libreoffice-bundled' for regex 'libreoffice*'
Note, selecting 'libreoffice-dbg' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-binfilter' for regex 'libreoffice*'
Note, selecting 'mozilla-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-ogltrans' for regex 'libreoffice*'
Note, selecting 'libreoffice-dev-doc' for regex 'libreoffice*'
Note, selecting 'libreoffice-dtd-officedocument1.0' for regex 'libreoffice*'
Note, selecting 'libreoffice-emailmerge' for regex 'libreoffice*'
Note, selecting 'libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk-gnome' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-3.3.2' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-gb' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-gb' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-us' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pt-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pt-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sv' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sv' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zh-tw' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zh-tw' for regex 'libreoffice*'
Note, selecting 'libreoffice-kab' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-3.3.2' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ast' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ast' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-be-by' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-be-by' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-ctl-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-or' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ta' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-te' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ku' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ku' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ns' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ns' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-or' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-rw' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-rw' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-si' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-si' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ss' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ss' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-st' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-st' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ta' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-te' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tg' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tg' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-th' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-th' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ts' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ts' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ug' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ug' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-uk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-uk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-uz' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-uz' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ve' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ve' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-vi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-vi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-xh' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-xh' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zu' for regex 'libreoffice*'
Note, selecting 'libreoffice-math' for regex 'libreoffice*'
Note, selecting 'libreoffice-nlpsolver' for regex 'libreoffice*'
Note, selecting 'libreoffice-voikko' for regex 'libreoffice*'
Note, selecting 'libreoffice-hyphenation-fi' for regex 'libreoffice*'
Note, selecting 'docvert-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-report-builder-bin' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-mobiledev' for regex 'libreoffice*'
Note, selecting 'openclipart-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-mysql-connector' for regex 'libreoffice*'
Note, selecting 'libreoffice-pdfimport' for regex 'libreoffice*'
Note, selecting 'libreoffice-presentation-minimizer' for regex 'libreoffice*'
Note, selecting 'libreoffice-presenter-console' for regex 'libreoffice*'
Note, selecting 'libreoffice-reportdesigner' for regex 'libreoffice*'
Note, selecting 'libreoffice-sdbc-postgresql' for regex 'libreoffice*'
Note, selecting 'libreoffice-wiki-publisher' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer2latex' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer2xhtml' for regex 'libreoffice*'
Note, selecting 'libreoffice-dmaths' for regex 'libreoffice*'
Note, selecting 'libreoffice-zemberek' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-3.3.3' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-3.3.3' for regex 'libreoffice*'
Note, selecting 'libreoffice3.3-mandriva-menus' for regex 'libreoffice*'
Note, selecting 'libreoffice3.3-redhat-menus' for regex 'libreoffice*'
Note, selecting 'libreoffice3.3-suse-menus' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-human' instead of 'libreoffice-style-default'
Note, selecting 'libreoffice-common' instead of 'libreoffice-l10n-en-us'
Note, selecting 'libreoffice-core' instead of 'libreoffice-bundled'
Note, selecting 'openoffice.org-dtd-officedocument1.0' instead of 'libreoffice-dtd-officedocument1.0'
Note, selecting 'libreoffice-gnome' instead of 'libreoffice-gtk-gnome'
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-spellcheck-fi'
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-hyphenation-fi'
Note, selecting 'libreoffice-report-builder' instead of 'libreoffice-reportdesigner'
Package libreoffice-nlpsolver is not installed, so not removed
Package libreoffice-voikko is not installed, so not removed
Package docvert-libreoffice is not installed, so not removed
Package libreoffice-writer2latex is not installed, so not removed
Package libreoffice-writer2xhtml is not installed, so not removed
Package libreoffice-dbg is not installed, so not removed
Package libreoffice-dev is not installed, so not removed
Package libreoffice-dev-doc is not installed, so not removed
Package libreoffice-filter-binfilter is not installed, so not removed
Package libreoffice-gcj is not installed, so not removed
Package libreoffice-gnome is not installed, so not removed
Package libreoffice-gtk is not installed, so not removed
Package libreoffice-help-ca is not installed, so not removed
Package libreoffice-help-cs is not installed, so not removed
Package libreoffice-help-da is not installed, so not removed
Package libreoffice-help-de is not installed, so not removed
Package libreoffice-help-dz is not installed, so not removed
Package libreoffice-help-el is not installed, so not removed
Package libreoffice-help-en-gb is not installed, so not removed
Package libreoffice-help-en-us is not installed, so not removed
Package libreoffice-help-es is not installed, so not removed
Package libreoffice-help-et is not installed, so not removed
Package libreoffice-help-eu is not installed, so not removed
Package libreoffice-help-fi is not installed, so not removed
Package libreoffice-help-fr is not installed, so not removed
Package libreoffice-help-gl is not installed, so not removed
Package libreoffice-help-hi is not installed, so not removed
Package libreoffice-help-hu is not installed, so not removed
Package libreoffice-help-it is not installed, so not removed
Package libreoffice-help-ja is not installed, so not removed
Package libreoffice-help-km is not installed, so not removed
Package libreoffice-help-ko is not installed, so not removed
Package libreoffice-help-nl is not installed, so not removed
Package libreoffice-help-om is not installed, so not removed
Package libreoffice-help-pl is not installed, so not removed
Package libreoffice-help-pt is not installed, so not removed
Package libreoffice-help-pt-br is not installed, so not removed
Package libreoffice-help-ru is not installed, so not removed
Package libreoffice-help-sk is not installed, so not removed
Package libreoffice-help-sl is not installed, so not removed
Package libreoffice-help-sv is not installed, so not removed
Package libreoffice-help-zh-cn is not installed, so not removed
Package libreoffice-help-zh-tw is not installed, so not removed
Package libreoffice-kde is not installed, so not removed
Package libreoffice-l10n-af is not installed, so not removed
Package libreoffice-l10n-ar is not installed, so not removed
Package libreoffice-l10n-as is not installed, so not removed
Package libreoffice-l10n-ast is not installed, so not removed
Package libreoffice-l10n-be-by is not installed, so not removed
Package libreoffice-l10n-bg is not installed, so not removed
Package libreoffice-l10n-bn is not installed, so not removed
Package libreoffice-l10n-br is not installed, so not removed
Package libreoffice-l10n-bs is not installed, so not removed
Package libreoffice-l10n-ca is not installed, so not removed
Package libreoffice-l10n-common is not installed, so not removed
Package libreoffice-l10n-cs is not installed, so not removed
Package libreoffice-l10n-cy is not installed, so not removed
Package libreoffice-l10n-da is not installed, so not removed
Package libreoffice-l10n-de is not installed, so not removed
Package libreoffice-l10n-dz is not installed, so not removed
Package libreoffice-l10n-el is not installed, so not removed
Package libreoffice-l10n-en-gb is not installed, so not removed
Package libreoffice-l10n-en-za is not installed, so not removed
Package libreoffice-l10n-eo is not installed, so not removed
Package libreoffice-l10n-es is not installed, so not removed
Package libreoffice-l10n-et is not installed, so not removed
Package libreoffice-l10n-eu is not installed, so not removed
Package libreoffice-l10n-fa is not installed, so not removed
Package libreoffice-l10n-fi is not installed, so not removed
Package libreoffice-l10n-fr is not installed, so not removed
Package libreoffice-l10n-ga is not installed, so not removed
Package libreoffice-l10n-gl is not installed, so not removed
Package libreoffice-l10n-gu is not installed, so not removed
Package libreoffice-l10n-he is not installed, so not removed
Package libreoffice-l10n-hi is not installed, so not removed
Package libreoffice-l10n-hr is not installed, so not removed
Package libreoffice-l10n-hu is not installed, so not removed
Package libreoffice-l10n-id is not installed, so not removed
Package libreoffice-l10n-in is not installed, so not removed
Package libreoffice-l10n-is is not installed, so not removed
Package libreoffice-l10n-it is not installed, so not removed
Package libreoffice-l10n-ja is not installed, so not removed
Package libreoffice-l10n-ka is not installed, so not removed
Package libreoffice-l10n-km is not installed, so not removed
Package libreoffice-l10n-ko is not installed, so not removed
Package libreoffice-l10n-ku is not installed, so not removed
Package libreoffice-l10n-lt is not installed, so not removed
Package libreoffice-l10n-lv is not installed, so not removed
Package libreoffice-l10n-mk is not installed, so not removed
Package libreoffice-l10n-ml is not installed, so not removed
Package libreoffice-l10n-mn is not installed, so not removed
Package libreoffice-l10n-mr is not installed, so not removed
Package libreoffice-l10n-nb is not installed, so not removed
Package libreoffice-l10n-ne is not installed, so not removed
Package libreoffice-l10n-nl is not installed, so not removed
Package libreoffice-l10n-nn is not installed, so not removed
Package libreoffice-l10n-nr is not installed, so not removed
Package libreoffice-l10n-ns is not installed, so not removed
Package libreoffice-l10n-oc is not installed, so not removed
Package libreoffice-l10n-om is not installed, so not removed
Package libreoffice-l10n-or is not installed, so not removed
Package libreoffice-l10n-pa-in is not installed, so not removed
Package libreoffice-l10n-pl is not installed, so not removed
Package libreoffice-l10n-pt is not installed, so not removed
Package libreoffice-l10n-pt-br is not installed, so not removed
Package libreoffice-l10n-ro is not installed, so not removed
Package libreoffice-l10n-ru is not installed, so not removed
Package libreoffice-l10n-rw is not installed, so not removed
Package libreoffice-l10n-si is not installed, so not removed
Package libreoffice-l10n-sk is not installed, so not removed
Package libreoffice-l10n-sl is not installed, so not removed
Package libreoffice-l10n-sr is not installed, so not removed
Package libreoffice-l10n-ss is not installed, so not removed
Package libreoffice-l10n-st is not installed, so not removed
Package libreoffice-l10n-sv is not installed, so not removed
Package libreoffice-l10n-ta is not installed, so not removed
Package libreoffice-l10n-te is not installed, so not removed
Package libreoffice-l10n-tg is not installed, so not removed
Package libreoffice-l10n-th is not installed, so not removed
Package libreoffice-l10n-tn is not installed, so not removed
Package libreoffice-l10n-tr is not installed, so not removed
Package libreoffice-l10n-ts is not installed, so not removed
Package libreoffice-l10n-ug is not installed, so not removed
Package libreoffice-l10n-uk is not installed, so not removed
Package libreoffice-l10n-uz is not installed, so not removed
Package libreoffice-l10n-ve is not installed, so not removed
Package libreoffice-l10n-vi is not installed, so not removed
Package libreoffice-l10n-xh is not installed, so not removed
Package libreoffice-l10n-za is not installed, so not removed
Package libreoffice-l10n-zh-cn is not installed, so not removed
Package libreoffice-l10n-zh-tw is not installed, so not removed
Package libreoffice-l10n-zu is not installed, so not removed
Package libreoffice-officebean is not installed, so not removed
Package libreoffice-style-andromeda is not installed, so not removed
Package libreoffice-style-oxygen is not installed, so not removed
Package libreoffice-style-tango is not installed, so not removed
Package libreoffice-evolution is not installed, so not removed
Package libreoffice-mysql-connector is not installed, so not removed
Package libreoffice-ogltrans is not installed, so not removed
Package libreoffice-pdfimport is not installed, so not removed
Package libreoffice-presentation-minimizer is not installed, so not removed
Package libreoffice-presenter-console is not installed, so not removed
Package libreoffice-report-builder is not installed, so not removed
Package libreoffice-sdbc-postgresql is not installed, so not removed
Package libreoffice-style-crystal is not installed, so not removed
Package libreoffice-style-galaxy is not installed, so not removed
Package libreoffice-style-hicontrast is not installed, so not removed
Package libreoffice-wiki-publisher is not installed, so not removed
Package mozilla-libreoffice is not installed, so not removed
Package openclipart-libreoffice is not installed, so not removed
Package openoffice.org-dtd-officedocument1.0 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  ttf-dejavu-extra ttf-sil-gentium libhsqldb-java libgif4 libservlet2.5-java
  ttf-sil-gentium-basic ttf-dejavu
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libreoffice* libreoffice-base* libreoffice-base-core* libreoffice-calc*
  libreoffice-common* libreoffice-core* libreoffice-draw*
  libreoffice-emailmerge* libreoffice-filter-mobiledev* libreoffice-impress*
  libreoffice-java-common* libreoffice-math* libreoffice-report-builder-bin*
  libreoffice-style-human* libreoffice-writer* python-uno*
0 upgraded, 0 newly installed, 16 to remove and 0 not upgraded.
After this operation, 261 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 188349 files and directories currently installed.)
Removing libreoffice ...
Removing libreoffice-report-builder-bin ...
Removing libreoffice-base ...
Purging configuration files for libreoffice-base ...
Removing libreoffice-writer ...
Purging configuration files for libreoffice-writer ...
Removing libreoffice-calc ...
Purging configuration files for libreoffice-calc ...
Removing libreoffice-base-core ...
Removing libreoffice-filter-mobiledev ...
Removing libreoffice-java-common ...
Removing libreoffice-emailmerge ...
Removing python-uno ...
Removing libreoffice-math ...
Purging configuration files for libreoffice-math ...
Removing libreoffice-impress ...
Purging configuration files for libreoffice-impress ...
Removing libreoffice-draw ...
Purging configuration files for libreoffice-draw ...
Removing libreoffice-common ...
Purging configuration files for libreoffice-common ...
Removing libreoffice-style-human ...
Removing libreoffice-core ...
Purging configuration files for libreoffice-core ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for shared-mime-info ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libreoffice-writer' for regex 'libreoffice*'
Note, selecting 'libreoffice-calc' for regex 'libreoffice*'
Note, selecting 'libreoffice-impress' for regex 'libreoffice*'
Note, selecting 'libreoffice-kde' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-oxygen' for regex 'libreoffice*'
Note, selecting 'libreoffice-base' for regex 'libreoffice*'
Note, selecting 'libreoffice-core' for regex 'libreoffice*'
Note, selecting 'libreoffice-base-core' for regex 'libreoffice*'
Note, selecting 'libreoffice-java-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-gcj' for regex 'libreoffice*'
Note, selecting 'libreoffice-report-builder' for regex 'libreoffice*'
Note, selecting 'libreoffice-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-default' for regex 'libreoffice*'
Note, selecting 'libreoffice-style' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-hicontrast' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-tango' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-crystal' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-human' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-andromeda' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-galaxy' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-industrial' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-us' for regex 'libreoffice*'
Note, selecting 'libreoffice-dev' for regex 'libreoffice*'
Note, selecting 'libreoffice-draw' for regex 'libreoffice*'
Note, selecting 'libreoffice-evolution' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-so52' for regex 'libreoffice*'
Note, selecting 'libreoffice-gnome' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk' for regex 'libreoffice*'
Note, selecting 'libreoffice-officebean' for regex 'libreoffice*'
Note, selecting 'libreoffice-bundled' for regex 'libreoffice*'
Note, selecting 'libreoffice-dbg' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-binfilter' for regex 'libreoffice*'
Note, selecting 'mozilla-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-ogltrans' for regex 'libreoffice*'
Note, selecting 'libreoffice-dev-doc' for regex 'libreoffice*'
Note, selecting 'libreoffice-dtd-officedocument1.0' for regex 'libreoffice*'
Note, selecting 'libreoffice-emailmerge' for regex 'libreoffice*'
Note, selecting 'libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk-gnome' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-3.3.2' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-gb' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-gb' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-us' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pt-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pt-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sv' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sv' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zh-tw' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zh-tw' for regex 'libreoffice*'
Note, selecting 'libreoffice-kab' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-3.3.2' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ast' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ast' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-be-by' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-be-by' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-ctl-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-or' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ta' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-te' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ku' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ku' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ns' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ns' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-or' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-rw' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-rw' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-si' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-si' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ss' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ss' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-st' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-st' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ta' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-te' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tg' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tg' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-th' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-th' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ts' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ts' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ug' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ug' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-uk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-uk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-uz' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-uz' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ve' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ve' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-vi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-vi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-xh' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-xh' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zu' for regex 'libreoffice*'
Note, selecting 'libreoffice-math' for regex 'libreoffice*'
Note, selecting 'libreoffice-nlpsolver' for regex 'libreoffice*'
Note, selecting 'libreoffice-voikko' for regex 'libreoffice*'
Note, selecting 'libreoffice-hyphenation-fi' for regex 'libreoffice*'
Note, selecting 'docvert-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-report-builder-bin' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-mobiledev' for regex 'libreoffice*'
Note, selecting 'openclipart-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-mysql-connector' for regex 'libreoffice*'
Note, selecting 'libreoffice-pdfimport' for regex 'libreoffice*'
Note, selecting 'libreoffice-presentation-minimizer' for regex 'libreoffice*'
Note, selecting 'libreoffice-presenter-console' for regex 'libreoffice*'
Note, selecting 'libreoffice-reportdesigner' for regex 'libreoffice*'
Note, selecting 'libreoffice-sdbc-postgresql' for regex 'libreoffice*'
Note, selecting 'libreoffice-wiki-publisher' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer2latex' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer2xhtml' for regex 'libreoffice*'
Note, selecting 'libreoffice-dmaths' for regex 'libreoffice*'
Note, selecting 'libreoffice-zemberek' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-3.3.3' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-3.3.3' for regex 'libreoffice*'
Note, selecting 'libreoffice3.3-mandriva-menus' for regex 'libreoffice*'
Note, selecting 'libreoffice3.3-redhat-menus' for regex 'libreoffice*'
Note, selecting 'libreoffice3.3-suse-menus' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-human' instead of 'libreoffice-style-default'
Note, selecting 'libreoffice-common' instead of 'libreoffice-l10n-en-us'
Note, selecting 'libreoffice-core' instead of 'libreoffice-bundled'
Note, selecting 'openoffice.org-dtd-officedocument1.0' instead of 'libreoffice-dtd-officedocument1.0'
Note, selecting 'libreoffice-gnome' instead of 'libreoffice-gtk-gnome'
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-spellcheck-fi'
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-hyphenation-fi'
Note, selecting 'libreoffice-report-builder' instead of 'libreoffice-reportdesigner'
The following extra packages will be installed:
  apache2-mpm-prefork apache2-utils apache2.2-bin apache2.2-common appmenu-qt
  aspell aspell-en bsh bsh-gcj culmus dictionaries-common dmake docbook-xsl
  docvert fckeditor gcj-4.5-base gcj-4.5-jre gcj-4.5-jre-headless
  gcj-4.5-jre-lib gcj-jre gcj-jre-headless icoutils jpegoptim kdebase-runtime
  kdebase-runtime-data kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools
  kubuntu-debug-installer libapache2-mod-php5 libapr1 libaprutil1
  libaprutil1-dbd-sqlite3 libaprutil1-ldap libattica0 libaudio2
  libbase-java-openoffice.org libclucene0ldbl libcommons-codec-java
  libcommons-httpclient-java libcommons-lang-java libcommons-logging-java
  libdbusmenu-qt2 libflute-java-openoffice.org libfonts-java-openoffice.org
  libformula-java-openoffice.org libgcj-bc libgcj-common libgcj11 libgcj11-awt
  libhsqldb-java-gcj libiodbc2 libjline-java libkatepartinterfaces4
  libkcmutils4 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4
  libkemoticons4 libkfile4 libkhtml5 libkidletime4 libkio5 libkjsapi4
  libkjsembed4 libkmediaplayer4 libknewstuff3-4 libknotifyconfig4 libkntlm4
  libkparts4 libkpty4 libkrosscore4 libktexteditor4
  liblayout-java-openoffice.org libloader-java-openoffice.org libmysqlclient16
  libmysqlcppconn4 libnepomuk4 libnepomukquery4a libnepomukutils4
  libntrack-qt4-1 libntrack0
  libpentaho-reporting-flow-engine-java-openoffice.org libphonon4
  libphp-pclzip libplasma3 libpolkit-qt-1-1 libpq5 libqapt-runtime libqapt1
  libqca2 libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl
  libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-xml
  libqt4-xmlpatterns libqtcore4 libqtgui4 libqtwebkit4 libreadline5
  librepository-java-openoffice.org librsvg2-bin libsac-java libsac-java-gcj
  libserializer-java-openoffice.org libsolid4 libsoprano4 libssh-4
  libstreamanalyzer0 libstreams0 libthreadweaver4 libtidy-0.99-0 libvirtodbc0
  libvoikko1 libxml-java-openoffice.org mysql-common ntrack-module-libnl-0
  openclipart-png optipng oxygen-icon-theme pdf2svg phonon
  phonon-backend-gstreamer php5-cli php5-common php5-gd php5-tidy php5-xsl
  plasma-scriptengine-declarative plasma-scriptengine-javascript pwgen
  python-uno qapt-batch shared-desktop-ontologies soprano-daemon ttf-arabeyes
  ttf-bengali-fonts ttf-devanagari-fonts ttf-dzongkha ttf-farsiweb
  ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-khmeros
  ttf-malayalam-fonts ttf-oriya-fonts ttf-tamil-fonts ttf-telugu-fonts
  uno-libs3-dbg ure-dbg virtuoso-minimal virtuoso-opensource-6.1-bin
  virtuoso-opensource-6.1-common voikko-fi
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom aspell-doc spellutils
  bsh-doc ispell emacsen-common jed-extra docbook-xsl-doc-html
  docbook-xsl-doc-pdf docbook-xsl-doc-text docbook-xsl-doc libsaxon-java
  libxalan2-java docbook-xsl-saxon fop xalan dbtoepub php5 fastjar gcj-4.5-jdk
  gcj-jdk libterm-readline-gnu-perl libterm-readline-perl-perl djvulibre-bin
  php-pear nas libcommons-httpclient-java-doc liblog4j1.2-java
  libexcalibur-logkit-java libavalon-framework-java
  libcommons-logging-java-doc libgcj11-dbg libhsqldb-java-doc
  libjline-java-doc hspell libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg
  libqca2-plugin-ossl libqca2-plugin-pkcs11 libqt4-dev qt4-qtconfig
  hunspell-dictionary myspell-dictionary libreoffice-help-3.3.3 menu
  hyphen-hyphenation-patterns mythes-thesaurus pstoedit imagemagick
  graphicsmagick-imagemagick-compat libmyodbc odbc-postgresql libsqliteodbc
  tdsodbc mdbtools libmysql-java libpg-java libjtds-java libssl0.9.8-dbg
  libdb4.8-dbg libc6-dbg libatk1.0-dbg libglib2.0-0-dbg libgnomevfs2-0-dbg
  libstdc++6-4.5-dbg libx11-6-dbg libxext6-dbg libxaw7-dbg libxml2-dbg
  libgtk2.0-0-dbg libxau6-dbg libice6-dbg libsm6-dbg libxinerama1-dbg
  libfontconfig1-dbg libcurl3-dbg python-dbg libnss3-1d-dbg libnspr4-0d-dbg
  mono-jit-dbg libmono0-dbg mono-dbg libxslt1-dbg kdelibs5-dbg libqt4-dbg
  libsuitesparse-dbg libgstreamer0.10-0-dbg libneon27-gnutls-dbg libmythes-dev
  libreoffice-dtd-officedocument1.0 konqueror kmail libreoffice-kab
  hunspell-dictionary-af myspell-dictionary-af hyphen-af mythes-af
  libreoffice-help-af hunspell-dictionary-ar myspell-dictionary-ar hyphen-ar
  mythes-ar libreoffice-help-ar hunspell-dictionary-as myspell-dictionary-as
  hyphen-as mythes-as libreoffice-help-as hunspell-dictionary-ast
  myspell-dictionary-ast hyphen-ast mythes-ast libreoffice-help-ast
  hunspell-dictionary-be-by myspell-dictionary-be-by hyphen-be-by mythes-be-by
  libreoffice-help-be-by hunspell-dictionary-bg myspell-dictionary-bg
  hyphen-bg mythes-bg libreoffice-help-bg hunspell-dictionary-bn
  myspell-dictionary-bn hyphen-bn mythes-bn libreoffice-help-bn
  hunspell-dictionary-br myspell-dictionary-br hyphen-br mythes-br
  libreoffice-help-br hunspell-dictionary-bs myspell-dictionary-bs hyphen-bs
  mythes-bs libreoffice-help-bs hunspell-dictionary-ca myspell-dictionary-ca
  hyphen-ca mythes-ca hunspell-dictionary-cs myspell-dictionary-cs hyphen-cs
  mythes-cs hunspell-dictionary-cy myspell-dictionary-cy hyphen-cy mythes-cy
  libreoffice-help-cy hunspell-dictionary-da myspell-dictionary-da hyphen-da
  mythes-da hunspell-dictionary-de myspell-dictionary-de hyphen-de mythes-de
  hunspell-dictionary-dz myspell-dictionary-dz hyphen-dz mythes-dz
  hunspell-dictionary-el myspell-dictionary-el hyphen-el mythes-el
  hunspell-dictionary-en-gb myspell-dictionary-en-gb hyphen-en-gb mythes-en-gb
  hunspell-dictionary-en-za myspell-dictionary-en-za hyphen-en-za mythes-en-za
  libreoffice-help-en-za hunspell-dictionary-eo myspell-dictionary-eo
  hyphen-eo mythes-eo libreoffice-help-eo hunspell-dictionary-es
  myspell-dictionary-es hyphen-es mythes-es hunspell-dictionary-et
  myspell-dictionary-et hyphen-et mythes-et hunspell-dictionary-eu
  myspell-dictionary-eu hyphen-eu mythes-eu hunspell-dictionary-fa
  myspell-dictionary-fa hyphen-fa mythes-fa libreoffice-help-fa
  hunspell-dictionary-fi myspell-dictionary-fi libreoffice-spellcheck-fi
  hyphen-fi mythes-fi hunspell-dictionary-fr myspell-dictionary-fr hyphen-fr
  mythes-fr hunspell-dictionary-ga myspell-dictionary-ga hyphen-ga mythes-ga
  libreoffice-help-ga hunspell-dictionary-gl myspell-dictionary-gl hyphen-gl
  mythes-gl hunspell-dictionary-gu myspell-dictionary-gu hyphen-gu mythes-gu
  libreoffice-help-gu hunspell-dictionary-he myspell-dictionary-he hyphen-he
  mythes-he libreoffice-help-he hunspell-dictionary-hi myspell-dictionary-hi
  hyphen-hi mythes-hi hunspell-dictionary-hr myspell-dictionary-hr hyphen-hr
  mythes-hr libreoffice-help-hr hunspell-dictionary-hu myspell-dictionary-hu
  hyphen-hu mythes-hu hunspell-dictionary-id myspell-dictionary-id hyphen-id
  mythes-id libreoffice-help-id hunspell-dictionary-is myspell-dictionary-is
  hyphen-is mythes-is libreoffice-help-is hunspell-dictionary-it
  myspell-dictionary-it hyphen-it mythes-it hunspell-dictionary-ja
  myspell-dictionary-ja hyphen-ja mythes-ja hunspell-dictionary-ka
  myspell-dictionary-ka hyphen-ka mythes-ka libreoffice-help-ka
  hunspell-dictionary-km myspell-dictionary-km hyphen-km mythes-km
  hunspell-dictionary-ko myspell-dictionary-ko hyphen-ko mythes-ko
  hunspell-dictionary-ku myspell-dictionary-ku hyphen-ku mythes-ku
  libreoffice-help-ku hunspell-dictionary-lt myspell-dictionary-lt hyphen-lt
  mythes-lt libreoffice-help-lt hunspell-dictionary-lv myspell-dictionary-lv
  hyphen-lv mythes-lv libreoffice-help-lv hunspell-dictionary-mk
  myspell-dictionary-mk hyphen-mk mythes-mk libreoffice-help-mk
  hunspell-dictionary-ml myspell-dictionary-ml hyphen-ml mythes-ml
  libreoffice-help-ml hunspell-dictionary-mn myspell-dictionary-mn hyphen-mn
  mythes-mn libreoffice-help-mn hunspell-dictionary-mr myspell-dictionary-mr
  hyphen-mr mythes-mr libreoffice-help-mr hunspell-dictionary-nb
  myspell-dictionary-nb hyphen-nb mythes-nb libreoffice-help-nb
  hunspell-dictionary-ne myspell-dictionary-ne hyphen-ne mythes-ne
  libreoffice-help-ne hunspell-dictionary-nl myspell-dictionary-nl hyphen-nl
  mythes-nl hunspell-dictionary-nn myspell-dictionary-nn hyphen-nn mythes-nn
  libreoffice-help-nn hunspell-dictionary-nr myspell-dictionary-nr hyphen-nr
  mythes-nr libreoffice-help-nr hunspell-dictionary-ns myspell-dictionary-ns
  hyphen-ns mythes-ns libreoffice-help-ns hunspell-dictionary-oc
  myspell-dictionary-oc hyphen-oc mythes-oc libreoffice-help-oc
  hunspell-dictionary-om myspell-dictionary-om hyphen-om mythes-om
  hunspell-dictionary-or myspell-dictionary-or hyphen-or mythes-or
  libreoffice-help-or hunspell-dictionary-pa-in myspell-dictionary-pa-in
  hyphen-pa-in mythes-pa-in libreoffice-help-pa-in hunspell-dictionary-pl
  myspell-dictionary-pl hyphen-pl mythes-pl hunspell-dictionary-pt
  myspell-dictionary-pt hyphen-pt mythes-pt hunspell-dictionary-pt-br
  myspell-dictionary-pt-br hyphen-pt-br mythes-pt-br hunspell-dictionary-ro
  myspell-dictionary-ro hyphen-ro mythes-ro libreoffice-help-ro
  hunspell-dictionary-ru myspell-dictionary-ru hyphen-ru mythes-ru
  hunspell-dictionary-rw myspell-dictionary-rw hyphen-rw mythes-rw
  libreoffice-help-rw hunspell-dictionary-si myspell-dictionary-si hyphen-si
  mythes-si libreoffice-help-si hunspell-dictionary-sk myspell-dictionary-sk
  hyphen-sk mythes-sk hunspell-dictionary-sl myspell-dictionary-sl hyphen-sl
  mythes-sl hunspell-dictionary-sr myspell-dictionary-sr hyphen-sr mythes-sr
  libreoffice-help-sr hunspell-dictionary-ss myspell-dictionary-ss hyphen-ss
  mythes-ss libreoffice-help-ss hunspell-dictionary-st myspell-dictionary-st
  hyphen-st mythes-st libreoffice-help-st hunspell-dictionary-sv
  myspell-dictionary-sv hyphen-sv mythes-sv hunspell-dictionary-ta
  myspell-dictionary-ta hyphen-ta mythes-ta libreoffice-help-ta
  hunspell-dictionary-te myspell-dictionary-te hyphen-te mythes-te
  libreoffice-help-te hunspell-dictionary-tg myspell-dictionary-tg hyphen-tg
  mythes-tg libreoffice-help-tg hunspell-dictionary-th myspell-dictionary-th
  hyphen-th mythes-th libreoffice-help-th hunspell-dictionary-tn
  myspell-dictionary-tn hyphen-tn mythes-tn libreoffice-help-tn
  hunspell-dictionary-tr myspell-dictionary-tr libreoffice-spellcheck-tr
  hyphen-tr mythes-tr libreoffice-help-tr hunspell-dictionary-ts
  myspell-dictionary-ts hyphen-ts mythes-ts libreoffice-help-ts
  hunspell-dictionary-ug myspell-dictionary-ug hyphen-ug mythes-ug
  libreoffice-help-ug hunspell-dictionary-uk myspell-dictionary-uk hyphen-uk
  mythes-uk libreoffice-help-uk hunspell-dictionary-uz myspell-dictionary-uz
  hyphen-uz mythes-uz libreoffice-help-uz hunspell-dictionary-ve
  myspell-dictionary-ve hyphen-ve mythes-ve libreoffice-help-ve
  hunspell-dictionary-vi myspell-dictionary-vi hyphen-vi mythes-vi
  libreoffice-help-vi hunspell-dictionary-xh myspell-dictionary-xh hyphen-xh
  mythes-xh libreoffice-help-xh hunspell-dictionary-zh-cn
  myspell-dictionary-zh-cn hyphen-zh-cn mythes-zh-cn hunspell-dictionary-zh-tw
  myspell-dictionary-zh-tw hyphen-zh-tw mythes-zh-tw hunspell-dictionary-zu
  myspell-dictionary-zu hyphen-zu mythes-zu libreoffice-help-zu mysql-server
  kde-icons-crystal crystalcursors kde-icons-oxygen oxygencursors
  tango-icon-theme mediawiki libsac-java-doc phonon-backend-xine
  phonon-backend-vlc phonon-backend-mplayer php5-suhosin xserver-xfree86
  xserver xfs
The following NEW packages will be installed:
  apache2-mpm-prefork apache2-utils apache2.2-bin apache2.2-common appmenu-qt
  aspell aspell-en bsh bsh-gcj culmus dictionaries-common dmake docbook-xsl
  docvert docvert-libreoffice fckeditor gcj-4.5-base gcj-4.5-jre
  gcj-4.5-jre-headless gcj-4.5-jre-lib gcj-jre gcj-jre-headless icoutils
  jpegoptim kdebase-runtime kdebase-runtime-data kdelibs-bin kdelibs5-data
  kdelibs5-plugins kdoctools kubuntu-debug-installer libapache2-mod-php5
  libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap libattica0
  libaudio2 libbase-java-openoffice.org libclucene0ldbl libcommons-codec-java
  libcommons-httpclient-java libcommons-lang-java libcommons-logging-java
  libdbusmenu-qt2 libflute-java-openoffice.org libfonts-java-openoffice.org
  libformula-java-openoffice.org libgcj-bc libgcj-common libgcj11 libgcj11-awt
  libhsqldb-java-gcj libiodbc2 libjline-java libkatepartinterfaces4
  libkcmutils4 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4
  libkemoticons4 libkfile4 libkhtml5 libkidletime4 libkio5 libkjsapi4
  libkjsembed4 libkmediaplayer4 libknewstuff3-4 libknotifyconfig4 libkntlm4
  libkparts4 libkpty4 libkrosscore4 libktexteditor4
  liblayout-java-openoffice.org libloader-java-openoffice.org libmysqlclient16
  libmysqlcppconn4 libnepomuk4 libnepomukquery4a libnepomukutils4
  libntrack-qt4-1 libntrack0
  libpentaho-reporting-flow-engine-java-openoffice.org libphonon4
  libphp-pclzip libplasma3 libpolkit-qt-1-1 libpq5 libqapt-runtime libqapt1
  libqca2 libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl
  libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-xml
  libqt4-xmlpatterns libqtcore4 libqtgui4 libqtwebkit4 libreadline5
  libreoffice libreoffice-base libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-dbg libreoffice-dev
  libreoffice-dev-doc libreoffice-draw libreoffice-emailmerge
  libreoffice-evolution libreoffice-filter-binfilter
  libreoffice-filter-mobiledev libreoffice-gcj libreoffice-gnome
  libreoffice-gtk libreoffice-help-ca libreoffice-help-cs libreoffice-help-da
  libreoffice-help-de libreoffice-help-dz libreoffice-help-el
  libreoffice-help-en-gb libreoffice-help-en-us libreoffice-help-es
  libreoffice-help-et libreoffice-help-eu libreoffice-help-fi
  libreoffice-help-fr libreoffice-help-gl libreoffice-help-hi
  libreoffice-help-hu libreoffice-help-it libreoffice-help-ja
  libreoffice-help-km libreoffice-help-ko libreoffice-help-nl
  libreoffice-help-om libreoffice-help-pl libreoffice-help-pt
  libreoffice-help-pt-br libreoffice-help-ru libreoffice-help-sk
  libreoffice-help-sl libreoffice-help-sv libreoffice-help-zh-cn
  libreoffice-help-zh-tw libreoffice-impress libreoffice-java-common
  libreoffice-kde libreoffice-l10n-af libreoffice-l10n-ar libreoffice-l10n-as
  libreoffice-l10n-ast libreoffice-l10n-be-by libreoffice-l10n-bg
  libreoffice-l10n-bn libreoffice-l10n-br libreoffice-l10n-bs
  libreoffice-l10n-ca libreoffice-l10n-common libreoffice-l10n-cs
  libreoffice-l10n-cy libreoffice-l10n-da libreoffice-l10n-de
  libreoffice-l10n-dz libreoffice-l10n-el libreoffice-l10n-en-gb
  libreoffice-l10n-en-za libreoffice-l10n-eo libreoffice-l10n-es
  libreoffice-l10n-et libreoffice-l10n-eu libreoffice-l10n-fa
  libreoffice-l10n-fi libreoffice-l10n-fr libreoffice-l10n-ga
  libreoffice-l10n-gl libreoffice-l10n-gu libreoffice-l10n-he
  libreoffice-l10n-hi libreoffice-l10n-hr libreoffice-l10n-hu
  libreoffice-l10n-id libreoffice-l10n-in libreoffice-l10n-is
  libreoffice-l10n-it libreoffice-l10n-ja libreoffice-l10n-ka
  libreoffice-l10n-km libreoffice-l10n-ko libreoffice-l10n-ku
  libreoffice-l10n-lt libreoffice-l10n-lv libreoffice-l10n-mk
  libreoffice-l10n-ml libreoffice-l10n-mn libreoffice-l10n-mr
  libreoffice-l10n-nb libreoffice-l10n-ne libreoffice-l10n-nl
  libreoffice-l10n-nn libreoffice-l10n-nr libreoffice-l10n-ns
  libreoffice-l10n-oc libreoffice-l10n-om libreoffice-l10n-or
  libreoffice-l10n-pa-in libreoffice-l10n-pl libreoffice-l10n-pt
  libreoffice-l10n-pt-br libreoffice-l10n-ro libreoffice-l10n-ru
  libreoffice-l10n-rw libreoffice-l10n-si libreoffice-l10n-sk
  libreoffice-l10n-sl libreoffice-l10n-sr libreoffice-l10n-ss
  libreoffice-l10n-st libreoffice-l10n-sv libreoffice-l10n-ta
  libreoffice-l10n-te libreoffice-l10n-tg libreoffice-l10n-th
  libreoffice-l10n-tn libreoffice-l10n-tr libreoffice-l10n-ts
  libreoffice-l10n-ug libreoffice-l10n-uk libreoffice-l10n-uz
  libreoffice-l10n-ve libreoffice-l10n-vi libreoffice-l10n-xh
  libreoffice-l10n-za libreoffice-l10n-zh-cn libreoffice-l10n-zh-tw
  libreoffice-l10n-zu libreoffice-math libreoffice-mysql-connector
  libreoffice-nlpsolver libreoffice-officebean libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-presentation-minimizer
  libreoffice-presenter-console libreoffice-report-builder
  libreoffice-report-builder-bin libreoffice-sdbc-postgresql
  libreoffice-style-andromeda libreoffice-style-crystal
  libreoffice-style-galaxy libreoffice-style-hicontrast
  libreoffice-style-human libreoffice-style-oxygen libreoffice-style-tango
  libreoffice-voikko libreoffice-wiki-publisher libreoffice-writer
  libreoffice-writer2latex libreoffice-writer2xhtml
  librepository-java-openoffice.org librsvg2-bin libsac-java libsac-java-gcj
  libserializer-java-openoffice.org libsolid4 libsoprano4 libssh-4
  libstreamanalyzer0 libstreams0 libthreadweaver4 libtidy-0.99-0 libvirtodbc0
  libvoikko1 libxml-java-openoffice.org mozilla-libreoffice mysql-common
  ntrack-module-libnl-0 openclipart-libreoffice openclipart-png
  openoffice.org-dtd-officedocument1.0 optipng oxygen-icon-theme pdf2svg
  phonon phonon-backend-gstreamer php5-cli php5-common php5-gd php5-tidy
  php5-xsl plasma-scriptengine-declarative plasma-scriptengine-javascript
  pwgen python-uno qapt-batch shared-desktop-ontologies soprano-daemon
  ttf-arabeyes ttf-bengali-fonts ttf-devanagari-fonts ttf-dzongkha
  ttf-farsiweb ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts
  ttf-khmeros ttf-malayalam-fonts ttf-oriya-fonts ttf-tamil-fonts
  ttf-telugu-fonts uno-libs3-dbg ure-dbg virtuoso-minimal
  virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common voikko-fi
0 upgraded, 328 newly installed, 0 to remove and 0 not upgraded.
Need to get 229 MB/711 MB of archives.
After this operation, 2,468 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-ku all 1:3.3.3-1ubuntu1 [1,642 kB]
Get:2 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-lt all 1:3.3.3-1ubuntu1 [1,631 kB]
Get:3 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-lv all 1:3.3.3-1ubuntu1 [1,634 kB]
Get:4 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-mk all 1:3.3.3-1ubuntu1 [1,650 kB]
Get:5 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-mn all 1:3.3.3-1ubuntu1 [1,659 kB]
Get:6 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-nb all 1:3.3.3-1ubuntu1 [1,624 kB]
Get:7 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-ne all 1:3.3.3-1ubuntu1 [1,649 kB]
Get:8 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-ne all 1:3.3.3-1ubuntu1 [1,649 kB]
Get:9 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-nn all 1:3.3.3-1ubuntu1 [1,626 kB]
Get:10 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-nr all 1:3.3.3-1ubuntu1 [1,636 kB]
Get:11 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-nr all 1:3.3.3-1ubuntu1 [1,636 kB]
Get:12 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-ns all 1:3.3.3-1ubuntu1 [1,639 kB]
Get:13 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-oc all 1:3.3.3-1ubuntu1 [1,638 kB]
Get:14 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-ro all 1:3.3.3-1ubuntu1 [1,634 kB]
Get:15 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-rw all 1:3.3.3-1ubuntu1 [1,632 kB]
Get:16 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-si all 1:3.3.3-1ubuntu1 [1,655 kB]
Get:17 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-sr all 1:3.3.3-1ubuntu1 [1,644 kB]
Get:18 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-sr all 1:3.3.3-1ubuntu1 [1,644 kB]
Get:19 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-ss all 1:3.3.3-1ubuntu1 [1,631 kB]
Get:20 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-st all 1:3.3.3-1ubuntu1 [1,631 kB]
Get:21 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-tg all 1:3.3.3-1ubuntu1 [1,638 kB]
Get:22 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-th all 1:3.3.3-1ubuntu1 [1,644 kB]
Get:23 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-tn all 1:3.3.3-1ubuntu1 [1,611 kB]
Get:24 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-tn all 1:3.3.3-1ubuntu1 [1,611 kB]
Get:25 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-tr all 1:3.3.3-1ubuntu1 [1,575 kB]
Get:26 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-ts all 1:3.3.3-1ubuntu1 [1,631 kB]
Get:27 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-ug all 1:3.3.3-1ubuntu1 [1,635 kB]
Get:28 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-uk all 1:3.3.3-1ubuntu1 [1,647 kB]
Get:29 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-uz all 1:3.3.3-1ubuntu1 [1,618 kB]
Get:30 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-ve all 1:3.3.3-1ubuntu1 [1,632 kB]
Get:31 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-ve all 1:3.3.3-1ubuntu1 [1,632 kB]
Get:32 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-vi all 1:3.3.3-1ubuntu1 [1,777 kB]
Get:33 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-xh all 1:3.3.3-1ubuntu1 [1,639 kB]
Get:34 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-zu all 1:3.3.3-1ubuntu1 [1,631 kB]
Get:35 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-l10n-za all 1:3.3.3-1ubuntu2 [2,712 B]
Get:36 http://de.archive.ubuntu.com/ubuntu/ natty-updates/universe libreoffice-mysql-connector amd64 1.0.1+LibO3.3.3-1ubuntu2 [95.8 kB]
Get:37 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-officebean amd64 1:3.3.3-1ubuntu2 [45.0 kB]
Get:38 http://de.archive.ubuntu.com/ubuntu/ natty-updates/universe libreoffice-presentation-minimizer amd64 1.0.3+LibO3.3.3-1ubuntu2 [142 kB]
Get:39 http://de.archive.ubuntu.com/ubuntu/ natty-updates/universe libreoffice-presenter-console amd64 1.1.0+LibO3.3.3-1ubuntu2 [328 kB]
Get:40 http://de.archive.ubuntu.com/ubuntu/ natty-updates/universe libreoffice-sdbc-postgresql amd64 1:0.7.6+LibO3.3.3-1ubuntu2 [206 kB]
Get:41 http://de.archive.ubuntu.com/ubuntu/ natty/main libvoikko1 amd64 3.1-1 [94.5 kB]
Get:42 http://de.archive.ubuntu.com/ubuntu/ natty/main voikko-fi amd64 1.8-1 [1,240 kB]
Get:43 http://de.archive.ubuntu.com/ubuntu/ natty/main libreoffice-voikko amd64 3.2~rc2-1 [67.5 kB]
Get:44 http://de.archive.ubuntu.com/ubuntu/ natty/universe libreoffice-writer2latex all 1.0.2-3ubuntu1 [371 kB]
Get:45 http://de.archive.ubuntu.com/ubuntu/ natty/universe libreoffice-writer2xhtml all 1.0.2-3ubuntu1 [291 kB]
Get:46 http://de.archive.ubuntu.com/ubuntu/ natty/main libsac-java-gcj amd64 1.3-3 [19.2 kB]
Get:47 http://de.archive.ubuntu.com/ubuntu/ natty/main virtuoso-opensource-6.1-common amd64 6.1.2+dfsg1-1ubuntu4 [46.9 kB]
Get:48 http://de.archive.ubuntu.com/ubuntu/ natty/main libvirtodbc0 amd64 6.1.2+dfsg1-1ubuntu4 [791 kB]
Get:49 http://de.archive.ubuntu.com/ubuntu/ natty-updates/universe mozilla-libreoffice amd64 1:3.3.3-1ubuntu2 [32.2 kB]
Get:50 http://de.archive.ubuntu.com/ubuntu/ natty/main optipng amd64 0.6.4-1 [88.5 kB]
Get:51 http://de.archive.ubuntu.com/ubuntu/ natty/main ttf-arabeyes all 2.1-2 [2,307 kB]
Get:52 http://de.archive.ubuntu.com/ubuntu/ natty/main ttf-bengali-fonts all 1:0.5.11ubuntu1 [322 kB]
Get:53 http://de.archive.ubuntu.com/ubuntu/ natty/main ttf-devanagari-fonts all 1:0.5.11ubuntu1 [1,738 kB]
Get:54 http://de.archive.ubuntu.com/ubuntu/ natty/main ttf-dzongkha all 0.3-6 [844 kB]
Get:55 http://de.archive.ubuntu.com/ubuntu/ natty/main ttf-farsiweb all 0.4.dfsg-9 [137 kB]
Get:56 http://de.archive.ubuntu.com/ubuntu/ natty/main ttf-gujarati-fonts all 1:0.5.11ubuntu1 [200 kB]
Get:57 http://de.archive.ubuntu.com/ubuntu/ natty/main ttf-kannada-fonts all 1:0.5.11ubuntu1 [301 kB]
Get:58 http://de.archive.ubuntu.com/ubuntu/ natty/main ttf-malayalam-fonts all 1:0.5.11ubuntu1 [515 kB]
Get:59 http://de.archive.ubuntu.com/ubuntu/ natty/main ttf-malayalam-fonts all 1:0.5.11ubuntu1 [515 kB]
Get:60 http://de.archive.ubuntu.com/ubuntu/ natty/main ttf-oriya-fonts all 1:0.5.11ubuntu1 [113 kB]
Get:61 http://de.archive.ubuntu.com/ubuntu/ natty/main ttf-tamil-fonts all 1:0.5.11ubuntu1 [366 kB]
Get:62 http://de.archive.ubuntu.com/ubuntu/ natty/main ttf-telugu-fonts all 1:0.5.11ubuntu1 [57.0 kB]
Get:63 http://de.archive.ubuntu.com/ubuntu/ natty/main ttf-indic-fonts all 1:0.5.11ubuntu1 [1,598 B]
Get:64 http://de.archive.ubuntu.com/ubuntu/ natty/main ttf-khmeros all 5.0-3ubuntu1 [730 kB]
Get:65 http://de.archive.ubuntu.com/ubuntu/ natty/main virtuoso-opensource-6.1-bin amd64 6.1.2+dfsg1-1ubuntu4 [3,869 kB]
Get:66 http://de.archive.ubuntu.com/ubuntu/ natty/main virtuoso-minimal all 6.1.2+dfsg1-1ubuntu4 [29.8 kB]
Get:67 http://de.archive.ubuntu.com/ubuntu/ natty/main dmake amd64 1:4.12-2 [126 kB]
Get:68 http://de.archive.ubuntu.com/ubuntu/ natty-updates/universe libreoffice-ogltrans amd64 1:3.3.3-1ubuntu2 [41.5 kB]
Get:69 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main libreoffice-dbg amd64 1:3.3.3-1ubuntu2 [29.7 MB]
Get:70 http://de.archive.ubuntu.com/ubuntu/ natty/main libreoffice-nlpsolver all 0.9~beta1-5 [86.2 kB]
Get:71 http://de.archive.ubuntu.com/ubuntu/ natty-updates/universe libreoffice-pdfimport amd64 1.0.3+LibO3.3.3-1ubuntu2 [395 kB]
Get:72 http://de.archive.ubuntu.com/ubuntu/ natty-updates/universe libreoffice-pdfimport amd64 1.0.3+LibO3.3.3-1ubuntu2 [395 kB]
Get:73 http://de.archive.ubuntu.com/ubuntu/ natty-updates/universe openclipart-png all 0.18+dfsg-10ubuntu1 [126 MB]
Get:74 http://de.archive.ubuntu.com/ubuntu/ natty-updates/universe openclipart-libreoffice all 0.18+dfsg-10ubuntu1 [8,859 kB]
Get:75 http://de.archive.ubuntu.com/ubuntu/ natty-updates/universe openclipart-libreoffice all 0.18+dfsg-10ubuntu1 [8,859 kB]
Get:76 http://de.archive.ubuntu.com/ubuntu/ natty-updates/universe openoffice.org-dtd-officedocument1.0 all 2:1.0+LibO3.3.3-1ubuntu2 [33.3 kB]
Get:77 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main uno-libs3-dbg amd64 1.7.0+LibO3.3.3-1ubuntu2 [175 kB]
Get:78 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main ure-dbg amd64 1.7.0+LibO3.3.3-1ubuntu2 [419 kB]
Fetched 224 MB in 14min 59s (249 kB/s)                                         
Extracting templates from packages: 100%
Preconfiguring packages ...
Selecting previously deselected package kdelibs5-data.
(Reading database ... 185601 files and directories currently installed.)
Unpacking kdelibs5-data (from .../kdelibs5-data_4%3a4.6.2-0ubuntu4_all.deb) ...
Selecting previously deselected package libgcj-common.
Unpacking libgcj-common (from .../libgcj-common_1%3a4.5.2-1ubuntu3_all.deb) ...
Selecting previously deselected package gcj-4.5-base.
Unpacking gcj-4.5-base (from .../gcj-4.5-base_4.5.2-8ubuntu1_amd64.deb) ...
Selecting previously deselected package libgcj11.
Unpacking libgcj11 (from .../libgcj11_4.5.2-8ubuntu1_amd64.deb) ...
Selecting previously deselected package gcj-4.5-jre-headless.
Unpacking gcj-4.5-jre-headless (from .../gcj-4.5-jre-headless_4.5.2-8ubuntu1_amd64.deb) ...
Selecting previously deselected package gcj-jre-headless.
Unpacking gcj-jre-headless (from .../gcj-jre-headless_4%3a4.5.2-1ubuntu3_amd64.deb) ...
Selecting previously deselected package libgcj11-awt.
Unpacking libgcj11-awt (from .../libgcj11-awt_4.5.2-8ubuntu1_amd64.deb) ...
Selecting previously deselected package gcj-4.5-jre.
Unpacking gcj-4.5-jre (from .../gcj-4.5-jre_4.5.2-8ubuntu1_amd64.deb) ...
Selecting previously deselected package gcj-jre.
Unpacking gcj-jre (from .../gcj-jre_4%3a4.5.2-1ubuntu3_amd64.deb) ...
Selecting previously deselected package libcommons-logging-java.
Unpacking libcommons-logging-java (from .../libcommons-logging-java_1.1.1-8_all.deb) ...
Selecting previously deselected package libbase-java-openoffice.org.
Unpacking libbase-java-openoffice.org (from .../libbase-java-openoffice.org_1.0.0-OOo31-2ubuntu1_all.deb) ...
Selecting previously deselected package libsac-java.
Unpacking libsac-java (from .../libsac-java_1.3-3_all.deb) ...
Selecting previously deselected package libloader-java-openoffice.org.
Unpacking libloader-java-openoffice.org (from .../libloader-java-openoffice.org_1.0.0-OOo31-2ubuntu1_all.deb) ...
Selecting previously deselected package libxml-java-openoffice.org.
Unpacking libxml-java-openoffice.org (from .../libxml-java-openoffice.org_1.0.0-OOo31-2ubuntu1_all.deb) ...
Selecting previously deselected package libflute-java-openoffice.org.
Unpacking libflute-java-openoffice.org (from .../libflute-java-openoffice.org_1.3.0-OOo31-3ubuntu1_all.deb) ...
Selecting previously deselected package libfonts-java-openoffice.org.
Unpacking libfonts-java-openoffice.org (from .../libfonts-java-openoffice.org_1.0.0-OOo31-2ubuntu1_all.deb) ...
Selecting previously deselected package librepository-java-openoffice.org.
Unpacking librepository-java-openoffice.org (from .../librepository-java-openoffice.org_1.0.0-OOo31-2ubuntu1_all.deb) ...
Selecting previously deselected package liblayout-java-openoffice.org.
Unpacking liblayout-java-openoffice.org (from .../liblayout-java-openoffice.org_0.2.9-OOo31-3ubuntu1_all.deb) ...
Selecting previously deselected package libformula-java-openoffice.org.
Unpacking libformula-java-openoffice.org (from .../libformula-java-openoffice.org_0.2.0-OOo31-2ubuntu1_all.deb) ...
Selecting previously deselected package libserializer-java-openoffice.org.
Unpacking libserializer-java-openoffice.org (from .../libserializer-java-openoffice.org_1.0.0-OOo31-2ubuntu1_all.deb) ...
Selecting previously deselected package libpentaho-reporting-flow-engine-java-openoffice.org.
Unpacking libpentaho-reporting-flow-engine-java-openoffice.org (from .../libpentaho-reporting-flow-engine-java-openoffice.org_0.9.2-OOo31-3ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-style-human.
Unpacking libreoffice-style-human (from .../libreoffice-style-human_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-style-hicontrast.
Unpacking libreoffice-style-hicontrast (from .../libreoffice-style-hicontrast_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-style-galaxy.
Unpacking libreoffice-style-galaxy (from .../libreoffice-style-galaxy_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-style-crystal.
Unpacking libreoffice-style-crystal (from .../libreoffice-style-crystal_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-style-tango.
Unpacking libreoffice-style-tango (from .../libreoffice-style-tango_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-style-oxygen.
Unpacking libreoffice-style-oxygen (from .../libreoffice-style-oxygen_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-style-andromeda.
Unpacking libreoffice-style-andromeda (from .../libreoffice-style-andromeda_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-common.
Unpacking libreoffice-common (from .../libreoffice-common_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-core.
Unpacking libreoffice-core (from .../libreoffice-core_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-base-core.
Unpacking libreoffice-base-core (from .../libreoffice-base-core_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-java-common.
Unpacking libreoffice-java-common (from .../libreoffice-java-common_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-base.
Unpacking libreoffice-base (from .../libreoffice-base_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-report-builder-bin.
Unpacking libreoffice-report-builder-bin (from .../libreoffice-report-builder-bin_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up libgcj-common (1:4.5.2-1ubuntu3) ...
Setting up gcj-4.5-base (4.5.2-8ubuntu1) ...
Setting up libgcj11 (4.5.2-8ubuntu1) ...
Setting up gcj-4.5-jre-headless (4.5.2-8ubuntu1) ...
Setting up gcj-jre-headless (4:4.5.2-1ubuntu3) ...
Setting up libgcj11-awt (4.5.2-8ubuntu1) ...
Setting up gcj-4.5-jre (4.5.2-8ubuntu1) ...
Setting up gcj-jre (4:4.5.2-1ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package libreoffice-report-builder.
(Reading database ... 188985 files and directories currently installed.)
Unpacking libreoffice-report-builder (from .../libreoffice-report-builder_1%3a1.2.1+LibO3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libcommons-codec-java.
Unpacking libcommons-codec-java (from .../libcommons-codec-java_1.4-2_all.deb) ...
Selecting previously deselected package libcommons-httpclient-java.
Unpacking libcommons-httpclient-java (from .../libcommons-httpclient-java_3.1-9_all.deb) ...
Selecting previously deselected package libcommons-lang-java.
Unpacking libcommons-lang-java (from .../libcommons-lang-java_2.4-4_all.deb) ...
Selecting previously deselected package libreoffice-wiki-publisher.
Unpacking libreoffice-wiki-publisher (from .../libreoffice-wiki-publisher_1.1.1+LibO3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package pwgen.
Unpacking pwgen (from .../pwgen_2.06-1ubuntu2_amd64.deb) ...
Selecting previously deselected package php5-common.
Unpacking php5-common (from .../php5-common_5.3.5-1ubuntu7.2_amd64.deb) ...
Selecting previously deselected package php5-cli.
Unpacking php5-cli (from .../php5-cli_5.3.5-1ubuntu7.2_amd64.deb) ...
Selecting previously deselected package libapr1.
Unpacking libapr1 (from .../libapr1_1.4.2-7ubuntu2.1_amd64.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.3.9+dfsg-5ubuntu3_amd64.deb) ...
Selecting previously deselected package libaprutil1-dbd-sqlite3.
Unpacking libaprutil1-dbd-sqlite3 (from .../libaprutil1-dbd-sqlite3_1.3.9+dfsg-5ubuntu3_amd64.deb) ...
Selecting previously deselected package libaprutil1-ldap.
Unpacking libaprutil1-ldap (from .../libaprutil1-ldap_1.3.9+dfsg-5ubuntu3_amd64.deb) ...
Selecting previously deselected package apache2.2-bin.
Unpacking apache2.2-bin (from .../apache2.2-bin_2.2.17-1ubuntu1_amd64.deb) ...
Selecting previously deselected package apache2-utils.
Unpacking apache2-utils (from .../apache2-utils_2.2.17-1ubuntu1_amd64.deb) ...
Selecting previously deselected package apache2.2-common.
Unpacking apache2.2-common (from .../apache2.2-common_2.2.17-1ubuntu1_amd64.deb) ...
Selecting previously deselected package apache2-mpm-prefork.
Unpacking apache2-mpm-prefork (from .../apache2-mpm-prefork_2.2.17-1ubuntu1_amd64.deb) ...
Selecting previously deselected package libapache2-mod-php5.
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.3.5-1ubuntu7.2_amd64.deb) ...
Selecting previously deselected package php5-xsl.
Unpacking php5-xsl (from .../php5-xsl_5.3.5-1ubuntu7.2_amd64.deb) ...
Selecting previously deselected package php5-gd.
Unpacking php5-gd (from .../php5-gd_5.3.5-1ubuntu7.2_amd64.deb) ...
Selecting previously deselected package libtidy-0.99-0.
Unpacking libtidy-0.99-0 (from .../libtidy-0.99-0_20091223cvs-1_amd64.deb) ...
Selecting previously deselected package php5-tidy.
Unpacking php5-tidy (from .../php5-tidy_5.3.5-1ubuntu7.2_amd64.deb) ...
Selecting previously deselected package librsvg2-bin.
Unpacking librsvg2-bin (from .../librsvg2-bin_2.32.1-0ubuntu3_amd64.deb) ...
Selecting previously deselected package libphp-pclzip.
Unpacking libphp-pclzip (from .../libphp-pclzip_2.8.2-2_all.deb) ...
Selecting previously deselected package fckeditor.
Unpacking fckeditor (from .../fckeditor_1%3a2.6.6-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up pwgen (2.06-1ubuntu2) ...
Selecting previously deselected package docvert.
(Reading database ... 190348 files and directories currently installed.)
Unpacking docvert (from .../archives/docvert_4.0-2_all.deb) ...
Selecting previously deselected package libreoffice-writer.
Unpacking libreoffice-writer (from .../libreoffice-writer_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package python-uno.
Unpacking python-uno (from .../python-uno_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package pdf2svg.
Unpacking pdf2svg (from .../pdf2svg_0.2.1-2build3_amd64.deb) ...
Selecting previously deselected package docvert-libreoffice.
Unpacking docvert-libreoffice (from .../docvert-libreoffice_4.0-2_all.deb) ...
Selecting previously deselected package libqtcore4.
Unpacking libqtcore4 (from .../libqtcore4_4%3a4.7.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package libqt4-xml.
Unpacking libqt4-xml (from .../libqt4-xml_4%3a4.7.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package libqt4-dbus.
Unpacking libqt4-dbus (from .../libqt4-dbus_4%3a4.7.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package libaudio2.
Unpacking libaudio2 (from .../libaudio2_1.9.2-4ubuntu1_amd64.deb) ...
Selecting previously deselected package libqtgui4.
Unpacking libqtgui4 (from .../libqtgui4_4%3a4.7.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package libdbusmenu-qt2.
Unpacking libdbusmenu-qt2 (from .../libdbusmenu-qt2_0.8.2-0ubuntu2_amd64.deb) ...
Selecting previously deselected package appmenu-qt.
Unpacking appmenu-qt (from .../appmenu-qt_0.1.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package dictionaries-common.
Unpacking dictionaries-common (from .../dictionaries-common_1.9.3ubuntu1_all.deb) ...
Adding 'diversion of /usr/share/dict/words to /usr/share/dict/words.pre-dictionaries-common by dictionaries-common'
Selecting previously deselected package aspell.
Unpacking aspell (from .../aspell_0.60.6-6_amd64.deb) ...
Selecting previously deselected package aspell-en.
Unpacking aspell-en (from .../aspell-en_6.0-0-6ubuntu1_all.deb) ...
Selecting previously deselected package libjline-java.
Unpacking libjline-java (from .../libjline-java_0.9.94-5_all.deb) ...
Selecting previously deselected package bsh.
Unpacking bsh (from .../archives/bsh_2.0b4-12_all.deb) ...
Selecting previously deselected package libgcj-bc.
Unpacking libgcj-bc (from .../libgcj-bc_4.5.2-1ubuntu3_amd64.deb) ...
Selecting previously deselected package bsh-gcj.
Unpacking bsh-gcj (from .../bsh-gcj_2.0b4-12_amd64.deb) ...
Selecting previously deselected package culmus.
Unpacking culmus (from .../culmus_0.110-1_all.deb) ...
Selecting previously deselected package docbook-xsl.
Unpacking docbook-xsl (from .../docbook-xsl_1.75.2+dfsg-5ubuntu1_all.deb) ...
Selecting previously deselected package gcj-4.5-jre-lib.
Unpacking gcj-4.5-jre-lib (from .../gcj-4.5-jre-lib_4.5.2-8ubuntu1_all.deb) ...
Selecting previously deselected package icoutils.
Unpacking icoutils (from .../icoutils_0.29.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package jpegoptim.
Unpacking jpegoptim (from .../jpegoptim_1.2.3-2_amd64.deb) ...
Selecting previously deselected package libqt4-network.
Unpacking libqt4-network (from .../libqt4-network_4%3a4.7.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package libattica0.
Unpacking libattica0 (from .../libattica0_0.2.80-0ubuntu2_amd64.deb) ...
Selecting previously deselected package libkdecore5.
Unpacking libkdecore5 (from .../libkdecore5_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libqt4-svg.
Unpacking libqt4-svg (from .../libqt4-svg_4%3a4.7.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package libkdeui5.
Unpacking libkdeui5 (from .../libkdeui5_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libkcmutils4.
Unpacking libkcmutils4 (from .../libkcmutils4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libkpty4.
Unpacking libkpty4 (from .../libkpty4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libkdesu5.
Unpacking libkdesu5 (from .../libkdesu5_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libkdnssd4.
Unpacking libkdnssd4 (from .../libkdnssd4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libclucene0ldbl.
Unpacking libclucene0ldbl (from .../libclucene0ldbl_0.9.21b-2_amd64.deb) ...
Selecting previously deselected package libiodbc2.
Unpacking libiodbc2 (from .../libiodbc2_3.52.6-4ubuntu1_amd64.deb) ...
Selecting previously deselected package soprano-daemon.
Unpacking soprano-daemon (from .../soprano-daemon_2.5.63+dfsg.1-0ubuntu1.1_amd64.deb) ...
Selecting previously deselected package libsoprano4.
Unpacking libsoprano4 (from .../libsoprano4_2.5.63+dfsg.1-0ubuntu1.1_amd64.deb) ...
Selecting previously deselected package libnepomuk4.
Unpacking libnepomuk4 (from .../libnepomuk4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libnepomukquery4a.
Unpacking libnepomukquery4a (from .../libnepomukquery4a_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libnepomukutils4.
Unpacking libnepomukutils4 (from .../libnepomukutils4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libsolid4.
Unpacking libsolid4 (from .../libsolid4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libstreams0.
Unpacking libstreams0 (from .../libstreams0_0.7.2-1ubuntu3_amd64.deb) ...
Selecting previously deselected package libstreamanalyzer0.
Unpacking libstreamanalyzer0 (from .../libstreamanalyzer0_0.7.2-1ubuntu3_amd64.deb) ...
Selecting previously deselected package libkio5.
Unpacking libkio5 (from .../libkio5_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libkemoticons4.
Unpacking libkemoticons4 (from .../libkemoticons4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libkfile4.
Unpacking libkfile4 (from .../libkfile4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libkjsapi4.
Unpacking libkjsapi4 (from .../libkjsapi4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libkparts4.
Unpacking libkparts4 (from .../libkparts4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libktexteditor4.
Unpacking libktexteditor4 (from .../libktexteditor4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libphonon4.
Unpacking libphonon4 (from .../libphonon4_4%3a4.7.0really4.5.0-0ubuntu3_amd64.deb) ...
Selecting previously deselected package libkhtml5.
Unpacking libkhtml5 (from .../libkhtml5_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libkidletime4.
Unpacking libkidletime4 (from .../libkidletime4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libkmediaplayer4.
Unpacking libkmediaplayer4 (from .../libkmediaplayer4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libknewstuff3-4.
Unpacking libknewstuff3-4 (from .../libknewstuff3-4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libknotifyconfig4.
Unpacking libknotifyconfig4 (from .../libknotifyconfig4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package ntrack-module-libnl-0.
Unpacking ntrack-module-libnl-0 (from .../ntrack-module-libnl-0_011-1ubuntu1.1_amd64.deb) ...
Selecting previously deselected package libntrack0.
Unpacking libntrack0 (from .../libntrack0_011-1ubuntu1.1_amd64.deb) ...
Selecting previously deselected package libntrack-qt4-1.
Unpacking libntrack-qt4-1 (from .../libntrack-qt4-1_011-1ubuntu1.1_amd64.deb) ...
Selecting previously deselected package libqt4-opengl.
Unpacking libqt4-opengl (from .../libqt4-opengl_4%3a4.7.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package phonon-backend-gstreamer.
Unpacking phonon-backend-gstreamer (from .../phonon-backend-gstreamer_4%3a4.7.0really4.5.0-0ubuntu2.1_amd64.deb) ...
Selecting previously deselected package phonon.
Unpacking phonon (from .../phonon_4%3a4.7.0really4.5.0-0ubuntu3_all.deb) ...
Selecting previously deselected package libqtwebkit4.
Unpacking libqtwebkit4 (from .../libqtwebkit4_2.1~really2.0.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libkdewebkit5.
Unpacking libkdewebkit5 (from .../libkdewebkit5_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libqca2.
Unpacking libqca2 (from .../libqca2_2.0.2-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libqt4-script.
Unpacking libqt4-script (from .../libqt4-script_4%3a4.7.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package libqt4-sql.
Unpacking libqt4-sql (from .../libqt4-sql_4%3a4.7.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package libqt4-xmlpatterns.
Unpacking libqt4-xmlpatterns (from .../libqt4-xmlpatterns_4%3a4.7.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package libqt4-declarative.
Unpacking libqt4-declarative (from .../libqt4-declarative_4%3a4.7.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package libthreadweaver4.
Unpacking libthreadweaver4 (from .../libthreadweaver4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libplasma3.
Unpacking libplasma3 (from .../libplasma3_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libssh-4.
Unpacking libssh-4 (from .../libssh-4_0.4.5-3ubuntu1_amd64.deb) ...
Selecting previously deselected package kdebase-runtime-data.
Unpacking kdebase-runtime-data (from .../kdebase-runtime-data_4%3a4.6.2-0ubuntu1_all.deb) ...
Selecting previously deselected package libkatepartinterfaces4.
Unpacking libkatepartinterfaces4 (from .../libkatepartinterfaces4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libkjsembed4.
Unpacking libkjsembed4 (from .../libkjsembed4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libkntlm4.
Unpacking libkntlm4 (from .../libkntlm4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libkrosscore4.
Unpacking libkrosscore4 (from .../libkrosscore4_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package libpolkit-qt-1-1.
Unpacking libpolkit-qt-1-1 (from .../libpolkit-qt-1-1_0.99.0-0ubuntu3_amd64.deb) ...
Selecting previously deselected package kdoctools.
Unpacking kdoctools (from .../kdoctools_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package kdelibs-bin.
Unpacking kdelibs-bin (from .../kdelibs-bin_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package kdelibs5-plugins.
Unpacking kdelibs5-plugins (from .../kdelibs5-plugins_4%3a4.6.2-0ubuntu4_amd64.deb) ...
Selecting previously deselected package oxygen-icon-theme.
Unpacking oxygen-icon-theme (from .../oxygen-icon-theme_4%3a4.6.2-0ubuntu1_all.deb) ...
Selecting previously deselected package shared-desktop-ontologies.
Unpacking shared-desktop-ontologies (from .../shared-desktop-ontologies_0.5-1_all.deb) ...
Selecting previously deselected package plasma-scriptengine-javascript.
Unpacking plasma-scriptengine-javascript (from .../plasma-scriptengine-javascript_4%3a4.6.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package plasma-scriptengine-declarative.
Unpacking plasma-scriptengine-declarative (from .../plasma-scriptengine-declarative_4%3a4.6.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package kdebase-runtime.
Unpacking kdebase-runtime (from .../kdebase-runtime_4%3a4.6.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libqapt1.
Unpacking libqapt1 (from .../libqapt1_1.1.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libqapt-runtime.
Unpacking libqapt-runtime (from .../libqapt-runtime_1.1.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package qapt-batch.
Unpacking qapt-batch (from .../qapt-batch_1.1.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package kubuntu-debug-installer.
Unpacking kubuntu-debug-installer (from .../kubuntu-debug-installer_11.04ubuntu1_amd64.deb) ...
Selecting previously deselected package libhsqldb-java-gcj.
Unpacking libhsqldb-java-gcj (from .../libhsqldb-java-gcj_1.8.0.10-9ubuntu1_amd64.deb) ...
Selecting previously deselected package mysql-common.
Unpacking mysql-common (from .../mysql-common_5.1.54-1ubuntu4_all.deb) ...
Selecting previously deselected package libmysqlclient16.
Unpacking libmysqlclient16 (from .../libmysqlclient16_5.1.54-1ubuntu4_amd64.deb) ...
Selecting previously deselected package libmysqlcppconn4.
Unpacking libmysqlcppconn4 (from .../libmysqlcppconn4_1.1.0~r814-1_amd64.deb) ...
Selecting previously deselected package libpq5.
Unpacking libpq5 (from .../libpq5_8.4.8-0ubuntu0.11.04_amd64.deb) ...
Selecting previously deselected package libqt4-sql-mysql.
Unpacking libqt4-sql-mysql (from .../libqt4-sql-mysql_4%3a4.7.2-0ubuntu6.2_amd64.deb) ...
Selecting previously deselected package libreadline5.
Unpacking libreadline5 (from .../libreadline5_5.2-7build1_amd64.deb) ...
Selecting previously deselected package libreoffice-calc.
Unpacking libreoffice-calc (from .../libreoffice-calc_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-draw.
Unpacking libreoffice-draw (from .../libreoffice-draw_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-impress.
Unpacking libreoffice-impress (from .../libreoffice-impress_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-math.
Unpacking libreoffice-math (from .../libreoffice-math_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-filter-mobiledev.
Unpacking libreoffice-filter-mobiledev (from .../libreoffice-filter-mobiledev_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice.
Unpacking libreoffice (from .../libreoffice_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-dev.
Unpacking libreoffice-dev (from .../libreoffice-dev_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-dev-doc.
Unpacking libreoffice-dev-doc (from .../libreoffice-dev-doc_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-emailmerge.
Unpacking libreoffice-emailmerge (from .../libreoffice-emailmerge_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-evolution.
Unpacking libreoffice-evolution (from .../libreoffice-evolution_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-filter-binfilter.
Unpacking libreoffice-filter-binfilter (from .../libreoffice-filter-binfilter_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-gcj.
Unpacking libreoffice-gcj (from .../libreoffice-gcj_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-gtk.
Unpacking libreoffice-gtk (from .../libreoffice-gtk_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-gnome.
Unpacking libreoffice-gnome (from .../libreoffice-gnome_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-l10n-common.
Unpacking libreoffice-l10n-common (from .../libreoffice-l10n-common_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ca.
Unpacking libreoffice-l10n-ca (from .../libreoffice-l10n-ca_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-ca.
Unpacking libreoffice-help-ca (from .../libreoffice-help-ca_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-cs.
Unpacking libreoffice-l10n-cs (from .../libreoffice-l10n-cs_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-cs.
Unpacking libreoffice-help-cs (from .../libreoffice-help-cs_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-da.
Unpacking libreoffice-l10n-da (from .../libreoffice-l10n-da_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-da.
Unpacking libreoffice-help-da (from .../libreoffice-help-da_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-de.
Unpacking libreoffice-l10n-de (from .../libreoffice-l10n-de_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-de.
Unpacking libreoffice-help-de (from .../libreoffice-help-de_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-dz.
Unpacking libreoffice-l10n-dz (from .../libreoffice-l10n-dz_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-dz.
Unpacking libreoffice-help-dz (from .../libreoffice-help-dz_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-el.
Unpacking libreoffice-l10n-el (from .../libreoffice-l10n-el_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-el.
Unpacking libreoffice-help-el (from .../libreoffice-help-el_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-en-gb.
Unpacking libreoffice-l10n-en-gb (from .../libreoffice-l10n-en-gb_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-en-gb.
Unpacking libreoffice-help-en-gb (from .../libreoffice-help-en-gb_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-en-us.
Unpacking libreoffice-help-en-us (from .../libreoffice-help-en-us_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-l10n-es.
Unpacking libreoffice-l10n-es (from .../libreoffice-l10n-es_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-es.
Unpacking libreoffice-help-es (from .../libreoffice-help-es_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-et.
Unpacking libreoffice-l10n-et (from .../libreoffice-l10n-et_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-et.
Unpacking libreoffice-help-et (from .../libreoffice-help-et_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-eu.
Unpacking libreoffice-l10n-eu (from .../libreoffice-l10n-eu_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-eu.
Unpacking libreoffice-help-eu (from .../libreoffice-help-eu_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-fi.
Unpacking libreoffice-l10n-fi (from .../libreoffice-l10n-fi_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-fi.
Unpacking libreoffice-help-fi (from .../libreoffice-help-fi_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-fr.
Unpacking libreoffice-l10n-fr (from .../libreoffice-l10n-fr_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-fr.
Unpacking libreoffice-help-fr (from .../libreoffice-help-fr_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-gl.
Unpacking libreoffice-l10n-gl (from .../libreoffice-l10n-gl_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-gl.
Unpacking libreoffice-help-gl (from .../libreoffice-help-gl_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-hi.
Unpacking libreoffice-l10n-hi (from .../libreoffice-l10n-hi_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-hi.
Unpacking libreoffice-help-hi (from .../libreoffice-help-hi_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-hu.
Unpacking libreoffice-l10n-hu (from .../libreoffice-l10n-hu_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-hu.
Unpacking libreoffice-help-hu (from .../libreoffice-help-hu_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-it.
Unpacking libreoffice-l10n-it (from .../libreoffice-l10n-it_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-it.
Unpacking libreoffice-help-it (from .../libreoffice-help-it_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ja.
Unpacking libreoffice-l10n-ja (from .../libreoffice-l10n-ja_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-ja.
Unpacking libreoffice-help-ja (from .../libreoffice-help-ja_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-km.
Unpacking libreoffice-l10n-km (from .../libreoffice-l10n-km_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-km.
Unpacking libreoffice-help-km (from .../libreoffice-help-km_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ko.
Unpacking libreoffice-l10n-ko (from .../libreoffice-l10n-ko_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-ko.
Unpacking libreoffice-help-ko (from .../libreoffice-help-ko_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-nl.
Unpacking libreoffice-l10n-nl (from .../libreoffice-l10n-nl_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-nl.
Unpacking libreoffice-help-nl (from .../libreoffice-help-nl_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-om.
Unpacking libreoffice-l10n-om (from .../libreoffice-l10n-om_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-om.
Unpacking libreoffice-help-om (from .../libreoffice-help-om_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-pl.
Unpacking libreoffice-l10n-pl (from .../libreoffice-l10n-pl_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-pl.
Unpacking libreoffice-help-pl (from .../libreoffice-help-pl_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-pt.
Unpacking libreoffice-l10n-pt (from .../libreoffice-l10n-pt_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-pt.
Unpacking libreoffice-help-pt (from .../libreoffice-help-pt_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-pt-br.
Unpacking libreoffice-l10n-pt-br (from .../libreoffice-l10n-pt-br_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-pt-br.
Unpacking libreoffice-help-pt-br (from .../libreoffice-help-pt-br_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ru.
Unpacking libreoffice-l10n-ru (from .../libreoffice-l10n-ru_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-ru.
Unpacking libreoffice-help-ru (from .../libreoffice-help-ru_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-sk.
Unpacking libreoffice-l10n-sk (from .../libreoffice-l10n-sk_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-sk.
Unpacking libreoffice-help-sk (from .../libreoffice-help-sk_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-sl.
Unpacking libreoffice-l10n-sl (from .../libreoffice-l10n-sl_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-sl.
Unpacking libreoffice-help-sl (from .../libreoffice-help-sl_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-sv.
Unpacking libreoffice-l10n-sv (from .../libreoffice-l10n-sv_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-sv.
Unpacking libreoffice-help-sv (from .../libreoffice-help-sv_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-zh-cn.
Unpacking libreoffice-l10n-zh-cn (from .../libreoffice-l10n-zh-cn_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-zh-cn.
Unpacking libreoffice-help-zh-cn (from .../libreoffice-help-zh-cn_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-zh-tw.
Unpacking libreoffice-l10n-zh-tw (from .../libreoffice-l10n-zh-tw_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-help-zh-tw.
Unpacking libreoffice-help-zh-tw (from .../libreoffice-help-zh-tw_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-kde.
Unpacking libreoffice-kde (from .../libreoffice-kde_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-l10n-af.
Unpacking libreoffice-l10n-af (from .../libreoffice-l10n-af_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ar.
Unpacking libreoffice-l10n-ar (from .../libreoffice-l10n-ar_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-as.
Unpacking libreoffice-l10n-as (from .../libreoffice-l10n-as_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ast.
Unpacking libreoffice-l10n-ast (from .../libreoffice-l10n-ast_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-be-by.
Unpacking libreoffice-l10n-be-by (from .../libreoffice-l10n-be-by_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-bg.
Unpacking libreoffice-l10n-bg (from .../libreoffice-l10n-bg_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-bn.
Unpacking libreoffice-l10n-bn (from .../libreoffice-l10n-bn_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-br.
Unpacking libreoffice-l10n-br (from .../libreoffice-l10n-br_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-bs.
Unpacking libreoffice-l10n-bs (from .../libreoffice-l10n-bs_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-cy.
Unpacking libreoffice-l10n-cy (from .../libreoffice-l10n-cy_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-en-za.
Unpacking libreoffice-l10n-en-za (from .../libreoffice-l10n-en-za_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-eo.
Unpacking libreoffice-l10n-eo (from .../libreoffice-l10n-eo_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-fa.
Unpacking libreoffice-l10n-fa (from .../libreoffice-l10n-fa_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ga.
Unpacking libreoffice-l10n-ga (from .../libreoffice-l10n-ga_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-gu.
Unpacking libreoffice-l10n-gu (from .../libreoffice-l10n-gu_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-he.
Unpacking libreoffice-l10n-he (from .../libreoffice-l10n-he_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-hr.
Unpacking libreoffice-l10n-hr (from .../libreoffice-l10n-hr_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-id.
Unpacking libreoffice-l10n-id (from .../libreoffice-l10n-id_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ml.
Unpacking libreoffice-l10n-ml (from .../libreoffice-l10n-ml_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-mr.
Unpacking libreoffice-l10n-mr (from .../libreoffice-l10n-mr_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-or.
Unpacking libreoffice-l10n-or (from .../libreoffice-l10n-or_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-pa-in.
Unpacking libreoffice-l10n-pa-in (from .../libreoffice-l10n-pa-in_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ta.
Unpacking libreoffice-l10n-ta (from .../libreoffice-l10n-ta_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-te.
Unpacking libreoffice-l10n-te (from .../libreoffice-l10n-te_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-in.
Unpacking libreoffice-l10n-in (from .../libreoffice-l10n-in_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-l10n-is.
Unpacking libreoffice-l10n-is (from .../libreoffice-l10n-is_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ka.
Unpacking libreoffice-l10n-ka (from .../libreoffice-l10n-ka_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ku.
Unpacking libreoffice-l10n-ku (from .../libreoffice-l10n-ku_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-lt.
Unpacking libreoffice-l10n-lt (from .../libreoffice-l10n-lt_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-lv.
Unpacking libreoffice-l10n-lv (from .../libreoffice-l10n-lv_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-mk.
Unpacking libreoffice-l10n-mk (from .../libreoffice-l10n-mk_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-mn.
Unpacking libreoffice-l10n-mn (from .../libreoffice-l10n-mn_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-nb.
Unpacking libreoffice-l10n-nb (from .../libreoffice-l10n-nb_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ne.
Unpacking libreoffice-l10n-ne (from .../libreoffice-l10n-ne_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-nn.
Unpacking libreoffice-l10n-nn (from .../libreoffice-l10n-nn_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-nr.
Unpacking libreoffice-l10n-nr (from .../libreoffice-l10n-nr_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ns.
Unpacking libreoffice-l10n-ns (from .../libreoffice-l10n-ns_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-oc.
Unpacking libreoffice-l10n-oc (from .../libreoffice-l10n-oc_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ro.
Unpacking libreoffice-l10n-ro (from .../libreoffice-l10n-ro_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-rw.
Unpacking libreoffice-l10n-rw (from .../libreoffice-l10n-rw_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-si.
Unpacking libreoffice-l10n-si (from .../libreoffice-l10n-si_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-sr.
Unpacking libreoffice-l10n-sr (from .../libreoffice-l10n-sr_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ss.
Unpacking libreoffice-l10n-ss (from .../libreoffice-l10n-ss_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-st.
Unpacking libreoffice-l10n-st (from .../libreoffice-l10n-st_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-tg.
Unpacking libreoffice-l10n-tg (from .../libreoffice-l10n-tg_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-th.
Unpacking libreoffice-l10n-th (from .../libreoffice-l10n-th_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-tn.
Unpacking libreoffice-l10n-tn (from .../libreoffice-l10n-tn_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-tr.
Unpacking libreoffice-l10n-tr (from .../libreoffice-l10n-tr_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ts.
Unpacking libreoffice-l10n-ts (from .../libreoffice-l10n-ts_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ug.
Unpacking libreoffice-l10n-ug (from .../libreoffice-l10n-ug_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-uk.
Unpacking libreoffice-l10n-uk (from .../libreoffice-l10n-uk_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-uz.
Unpacking libreoffice-l10n-uz (from .../libreoffice-l10n-uz_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-ve.
Unpacking libreoffice-l10n-ve (from .../libreoffice-l10n-ve_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-vi.
Unpacking libreoffice-l10n-vi (from .../libreoffice-l10n-vi_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-xh.
Unpacking libreoffice-l10n-xh (from .../libreoffice-l10n-xh_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-zu.
Unpacking libreoffice-l10n-zu (from .../libreoffice-l10n-zu_1%3a3.3.3-1ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-l10n-za.
Unpacking libreoffice-l10n-za (from .../libreoffice-l10n-za_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-mysql-connector.
Unpacking libreoffice-mysql-connector (from .../libreoffice-mysql-connector_1.0.1+LibO3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-officebean.
Unpacking libreoffice-officebean (from .../libreoffice-officebean_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-presentation-minimizer.
Unpacking libreoffice-presentation-minimizer (from .../libreoffice-presentation-minimizer_1.0.3+LibO3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-presenter-console.
Unpacking libreoffice-presenter-console (from .../libreoffice-presenter-console_1.1.0+LibO3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-sdbc-postgresql.
Unpacking libreoffice-sdbc-postgresql (from .../libreoffice-sdbc-postgresql_1%3a0.7.6+LibO3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libvoikko1.
Unpacking libvoikko1 (from .../libvoikko1_3.1-1_amd64.deb) ...
Selecting previously deselected package voikko-fi.
Unpacking voikko-fi (from .../voikko-fi_1.8-1_amd64.deb) ...
Selecting previously deselected package libreoffice-voikko.
Unpacking libreoffice-voikko (from .../libreoffice-voikko_3.2~rc2-1_amd64.deb) ...
Selecting previously deselected package libreoffice-writer2latex.
Unpacking libreoffice-writer2latex (from .../libreoffice-writer2latex_1.0.2-3ubuntu1_all.deb) ...
Selecting previously deselected package libreoffice-writer2xhtml.
Unpacking libreoffice-writer2xhtml (from .../libreoffice-writer2xhtml_1.0.2-3ubuntu1_all.deb) ...
Selecting previously deselected package libsac-java-gcj.
Unpacking libsac-java-gcj (from .../libsac-java-gcj_1.3-3_amd64.deb) ...
Selecting previously deselected package virtuoso-opensource-6.1-common.
Unpacking virtuoso-opensource-6.1-common (from .../virtuoso-opensource-6.1-common_6.1.2+dfsg1-1ubuntu4_amd64.deb) ...
Selecting previously deselected package libvirtodbc0.
Unpacking libvirtodbc0 (from .../libvirtodbc0_6.1.2+dfsg1-1ubuntu4_amd64.deb) ...
Selecting previously deselected package mozilla-libreoffice.
Unpacking mozilla-libreoffice (from .../mozilla-libreoffice_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package optipng.
Unpacking optipng (from .../optipng_0.6.4-1_amd64.deb) ...
Selecting previously deselected package ttf-arabeyes.
Unpacking ttf-arabeyes (from .../ttf-arabeyes_2.1-2_all.deb) ...
Selecting previously deselected package ttf-bengali-fonts.
Unpacking ttf-bengali-fonts (from .../ttf-bengali-fonts_1%3a0.5.11ubuntu1_all.deb) ...
Selecting previously deselected package ttf-devanagari-fonts.
Unpacking ttf-devanagari-fonts (from .../ttf-devanagari-fonts_1%3a0.5.11ubuntu1_all.deb) ...
Selecting previously deselected package ttf-dzongkha.
Unpacking ttf-dzongkha (from .../ttf-dzongkha_0.3-6_all.deb) ...
Selecting previously deselected package ttf-farsiweb.
Unpacking ttf-farsiweb (from .../ttf-farsiweb_0.4.dfsg-9_all.deb) ...
Selecting previously deselected package ttf-gujarati-fonts.
Unpacking ttf-gujarati-fonts (from .../ttf-gujarati-fonts_1%3a0.5.11ubuntu1_all.deb) ...
Selecting previously deselected package ttf-kannada-fonts.
Unpacking ttf-kannada-fonts (from .../ttf-kannada-fonts_1%3a0.5.11ubuntu1_all.deb) ...
Selecting previously deselected package ttf-malayalam-fonts.
Unpacking ttf-malayalam-fonts (from .../ttf-malayalam-fonts_1%3a0.5.11ubuntu1_all.deb) ...
Selecting previously deselected package ttf-oriya-fonts.
Unpacking ttf-oriya-fonts (from .../ttf-oriya-fonts_1%3a0.5.11ubuntu1_all.deb) ...
Selecting previously deselected package ttf-tamil-fonts.
Unpacking ttf-tamil-fonts (from .../ttf-tamil-fonts_1%3a0.5.11ubuntu1_all.deb) ...
Selecting previously deselected package ttf-telugu-fonts.
Unpacking ttf-telugu-fonts (from .../ttf-telugu-fonts_1%3a0.5.11ubuntu1_all.deb) ...
Selecting previously deselected package ttf-indic-fonts.
Unpacking ttf-indic-fonts (from .../ttf-indic-fonts_1%3a0.5.11ubuntu1_all.deb) ...
Selecting previously deselected package ttf-khmeros.
Unpacking ttf-khmeros (from .../ttf-khmeros_5.0-3ubuntu1_all.deb) ...
Selecting previously deselected package virtuoso-opensource-6.1-bin.
Unpacking virtuoso-opensource-6.1-bin (from .../virtuoso-opensource-6.1-bin_6.1.2+dfsg1-1ubuntu4_amd64.deb) ...
Selecting previously deselected package virtuoso-minimal.
Unpacking virtuoso-minimal (from .../virtuoso-minimal_6.1.2+dfsg1-1ubuntu4_all.deb) ...
Selecting previously deselected package dmake.
Unpacking dmake (from .../dmake_1%3a4.12-2_amd64.deb) ...
Selecting previously deselected package libreoffice-ogltrans.
Unpacking libreoffice-ogltrans (from .../libreoffice-ogltrans_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-dbg.
Unpacking libreoffice-dbg (from .../libreoffice-dbg_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-nlpsolver.
Unpacking libreoffice-nlpsolver (from .../libreoffice-nlpsolver_0.9~beta1-5_all.deb) ...
Selecting previously deselected package libreoffice-pdfimport.
Unpacking libreoffice-pdfimport (from .../libreoffice-pdfimport_1.0.3+LibO3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package openclipart-png.
Unpacking openclipart-png (from .../openclipart-png_0.18+dfsg-10ubuntu1_all.deb) ...
Selecting previously deselected package openclipart-libreoffice.
Unpacking openclipart-libreoffice (from .../openclipart-libreoffice_0.18+dfsg-10ubuntu1_all.deb) ...
Selecting previously deselected package openoffice.org-dtd-officedocument1.0.
Unpacking openoffice.org-dtd-officedocument1.0 (from .../openoffice.org-dtd-officedocument1.0_2%3a1.0+LibO3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package uno-libs3-dbg.
Unpacking uno-libs3-dbg (from .../uno-libs3-dbg_1.7.0+LibO3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package ure-dbg.
Unpacking ure-dbg (from .../ure-dbg_1.7.0+LibO3.3.3-1ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for ureadahead ...
Processing triggers for fontconfig ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for doc-base ...
Processing 4 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for python-support ...
Setting up kdelibs5-data (4:4.6.2-0ubuntu4) ...
Setting up libcommons-logging-java (1.1.1-8) ...
Setting up libbase-java-openoffice.org (1.0.0-OOo31-2ubuntu1) ...
Setting up libsac-java (1.3-3) ...
Setting up libloader-java-openoffice.org (1.0.0-OOo31-2ubuntu1) ...
Setting up libxml-java-openoffice.org (1.0.0-OOo31-2ubuntu1) ...
Setting up libflute-java-openoffice.org (1.3.0-OOo31-3ubuntu1) ...
Setting up libfonts-java-openoffice.org (1.0.0-OOo31-2ubuntu1) ...
Setting up librepository-java-openoffice.org (1.0.0-OOo31-2ubuntu1) ...
Setting up liblayout-java-openoffice.org (0.2.9-OOo31-3ubuntu1) ...
Setting up libformula-java-openoffice.org (0.2.0-OOo31-2ubuntu1) ...
Setting up libserializer-java-openoffice.org (1.0.0-OOo31-2ubuntu1) ...
Setting up libpentaho-reporting-flow-engine-java-openoffice.org (0.9.2-OOo31-3ubuntu1) ...
Setting up libcommons-codec-java (1.4-2) ...
Setting up libcommons-httpclient-java (3.1-9) ...
Setting up libcommons-lang-java (2.4-4) ...
Setting up php5-common (5.3.5-1ubuntu7.2) ...
Setting up php5-cli (5.3.5-1ubuntu7.2) ...

Creating config file /etc/php5/cli/php.ini with new version
update-alternatives: using /usr/bin/php5 to provide /usr/bin/php (php) in auto mode.
Setting up libapr1 (1.4.2-7ubuntu2.1) ...
Setting up libaprutil1 (1.3.9+dfsg-5ubuntu3) ...
Setting up libaprutil1-dbd-sqlite3 (1.3.9+dfsg-5ubuntu3) ...
Setting up libaprutil1-ldap (1.3.9+dfsg-5ubuntu3) ...
Setting up apache2.2-bin (2.2.17-1ubuntu1) ...
Setting up apache2-utils (2.2.17-1ubuntu1) ...
Setting up apache2.2-common (2.2.17-1ubuntu1) ...
Enabling site default.
Enabling module alias.
Enabling module autoindex.
Enabling module dir.
Enabling module env.
Enabling module mime.
Enabling module negotiation.
Enabling module setenvif.
Enabling module status.
Enabling module auth_basic.
Enabling module deflate.
Enabling module authz_default.
Enabling module authz_user.
Enabling module authz_groupfile.
Enabling module authn_file.
Enabling module authz_host.
Enabling module reqtimeout.
Setting up apache2-mpm-prefork (2.2.17-1ubuntu1) ...
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
Setting up libapache2-mod-php5 (5.3.5-1ubuntu7.2) ...

Creating config file /etc/php5/apache2/php.ini with new version
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
Setting up php5-xsl (5.3.5-1ubuntu7.2) ...
Setting up php5-gd (5.3.5-1ubuntu7.2) ...
Setting up libtidy-0.99-0 (20091223cvs-1) ...
Setting up php5-tidy (5.3.5-1ubuntu7.2) ...
Setting up librsvg2-bin (2.32.1-0ubuntu3) ...
Setting up libphp-pclzip (2.8.2-2) ...
Setting up fckeditor (1:2.6.6-1) ...
Setting up docvert (4.0-2) ...
Setting up pdf2svg (0.2.1-2build3) ...
Setting up libqtcore4 (4:4.7.2-0ubuntu6.2) ...
Setting up libqt4-xml (4:4.7.2-0ubuntu6.2) ...
Setting up libqt4-dbus (4:4.7.2-0ubuntu6.2) ...
Setting up libaudio2 (1.9.2-4ubuntu1) ...
Setting up libqtgui4 (4:4.7.2-0ubuntu6.2) ...
Setting up libdbusmenu-qt2 (0.8.2-0ubuntu2) ...
Setting up appmenu-qt (0.1.2-0ubuntu1) ...
Setting up dictionaries-common (1.9.3ubuntu1) ...
Setting up libjline-java (0.9.94-5) ...
Setting up bsh (2.0b4-12) ...
Setting up libgcj-bc (4.5.2-1ubuntu3) ...
Setting up bsh-gcj (2.0b4-12) ...
Setting up culmus (0.110-1) ...
Setting up docbook-xsl (1.75.2+dfsg-5ubuntu1) ...
Setting up gcj-4.5-jre-lib (4.5.2-8ubuntu1) ...
Setting up icoutils (0.29.1-0ubuntu1) ...
Setting up jpegoptim (1.2.3-2) ...
Setting up libqt4-network (4:4.7.2-0ubuntu6.2) ...
Setting up libattica0 (0.2.80-0ubuntu2) ...
Setting up libkdecore5 (4:4.6.2-0ubuntu4) ...
Setting up libqt4-svg (4:4.7.2-0ubuntu6.2) ...
Setting up libkdeui5 (4:4.6.2-0ubuntu4) ...
Setting up libkcmutils4 (4:4.6.2-0ubuntu4) ...
Setting up libkpty4 (4:4.6.2-0ubuntu4) ...
Setting up libkdesu5 (4:4.6.2-0ubuntu4) ...
Setting up libkdnssd4 (4:4.6.2-0ubuntu4) ...
Setting up libclucene0ldbl (0.9.21b-2) ...
Setting up libiodbc2 (3.52.6-4ubuntu1) ...
Setting up soprano-daemon (2.5.63+dfsg.1-0ubuntu1.1) ...
Setting up libsoprano4 (2.5.63+dfsg.1-0ubuntu1.1) ...
Setting up libnepomuk4 (4:4.6.2-0ubuntu4) ...
Setting up libnepomukquery4a (4:4.6.2-0ubuntu4) ...
Setting up libnepomukutils4 (4:4.6.2-0ubuntu4) ...
Setting up libsolid4 (4:4.6.2-0ubuntu4) ...
Setting up libstreams0 (0.7.2-1ubuntu3) ...
Setting up libstreamanalyzer0 (0.7.2-1ubuntu3) ...
Setting up libkio5 (4:4.6.2-0ubuntu4) ...
Setting up libkemoticons4 (4:4.6.2-0ubuntu4) ...
Setting up libkfile4 (4:4.6.2-0ubuntu4) ...
Setting up libkjsapi4 (4:4.6.2-0ubuntu4) ...
Setting up libkparts4 (4:4.6.2-0ubuntu4) ...
Setting up libktexteditor4 (4:4.6.2-0ubuntu4) ...
Setting up libphonon4 (4:4.7.0really4.5.0-0ubuntu3) ...
Setting up libkhtml5 (4:4.6.2-0ubuntu4) ...
Setting up libkidletime4 (4:4.6.2-0ubuntu4) ...
Setting up libkmediaplayer4 (4:4.6.2-0ubuntu4) ...
Setting up libknewstuff3-4 (4:4.6.2-0ubuntu4) ...
Setting up libknotifyconfig4 (4:4.6.2-0ubuntu4) ...
Setting up libqt4-opengl (4:4.7.2-0ubuntu6.2) ...
Setting up phonon-backend-gstreamer (4:4.7.0really4.5.0-0ubuntu2.1) ...
Setting up phonon (4:4.7.0really4.5.0-0ubuntu3) ...
Setting up libqtwebkit4 (2.1~really2.0.2-0ubuntu1) ...
Setting up libkdewebkit5 (4:4.6.2-0ubuntu4) ...
Setting up libqca2 (2.0.2-1ubuntu2) ...
Setting up libqt4-script (4:4.7.2-0ubuntu6.2) ...
Setting up libqt4-sql (4:4.7.2-0ubuntu6.2) ...
Setting up libqt4-xmlpatterns (4:4.7.2-0ubuntu6.2) ...
Setting up libqt4-declarative (4:4.7.2-0ubuntu6.2) ...
Setting up libthreadweaver4 (4:4.6.2-0ubuntu4) ...
Setting up libplasma3 (4:4.6.2-0ubuntu4) ...
Setting up libssh-4 (0.4.5-3ubuntu1) ...
Setting up kdebase-runtime-data (4:4.6.2-0ubuntu1) ...
Setting up libkatepartinterfaces4 (4:4.6.2-0ubuntu4) ...
Setting up libkjsembed4 (4:4.6.2-0ubuntu4) ...
Setting up libkntlm4 (4:4.6.2-0ubuntu4) ...
Setting up libkrosscore4 (4:4.6.2-0ubuntu4) ...
Setting up libpolkit-qt-1-1 (0.99.0-0ubuntu3) ...
Setting up kdoctools (4:4.6.2-0ubuntu4) ...
Setting up kdelibs-bin (4:4.6.2-0ubuntu4) ...
Setting up kdelibs5-plugins (4:4.6.2-0ubuntu4) ...
Setting up oxygen-icon-theme (4:4.6.2-0ubuntu1) ...
Setting up shared-desktop-ontologies (0.5-1) ...
Setting up plasma-scriptengine-javascript (4:4.6.2-0ubuntu1) ...
Setting up plasma-scriptengine-declarative (4:4.6.2-0ubuntu1) ...
Setting up libqapt1 (1.1.2-0ubuntu1) ...
Setting up libqapt-runtime (1.1.2-0ubuntu1) ...
Setting up libhsqldb-java-gcj (1.8.0.10-9ubuntu1) ...
Setting up mysql-common (5.1.54-1ubuntu4) ...
Setting up libmysqlclient16 (5.1.54-1ubuntu4) ...
Setting up libmysqlcppconn4 (1.1.0~r814-1) ...
Setting up libpq5 (8.4.8-0ubuntu0.11.04) ...
Setting up libqt4-sql-mysql (4:4.7.2-0ubuntu6.2) ...
Setting up libreadline5 (5.2-7build1) ...
Setting up libreoffice-dev-doc (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-l10n-common (1:3.3.3-1ubuntu1) ...
Setting up libvoikko1 (3.1-1) ...
Setting up voikko-fi (1.8-1) ...
Setting up libsac-java-gcj (1.3-3) ...
Setting up virtuoso-opensource-6.1-common (6.1.2+dfsg1-1ubuntu4) ...
Setting up libvirtodbc0 (6.1.2+dfsg1-1ubuntu4) ...
Setting up optipng (0.6.4-1) ...
Setting up ttf-arabeyes (2.1-2) ...
Setting up ttf-bengali-fonts (1:0.5.11ubuntu1) ...
Setting up ttf-devanagari-fonts (1:0.5.11ubuntu1) ...
Setting up ttf-dzongkha (0.3-6) ...
Setting up ttf-farsiweb (0.4.dfsg-9) ...
Setting up ttf-gujarati-fonts (1:0.5.11ubuntu1) ...
Setting up ttf-kannada-fonts (1:0.5.11ubuntu1) ...
Setting up ttf-malayalam-fonts (1:0.5.11ubuntu1) ...
Setting up ttf-oriya-fonts (1:0.5.11ubuntu1) ...
Setting up ttf-tamil-fonts (1:0.5.11ubuntu1) ...
Setting up ttf-telugu-fonts (1:0.5.11ubuntu1) ...
Setting up ttf-indic-fonts (1:0.5.11ubuntu1) ...
Setting up ttf-khmeros (5.0-3ubuntu1) ...
Setting up virtuoso-opensource-6.1-bin (6.1.2+dfsg1-1ubuntu4) ...
Setting up virtuoso-minimal (6.1.2+dfsg1-1ubuntu4) ...
Setting up dmake (1:4.12-2) ...
Setting up openclipart-png (0.18+dfsg-10ubuntu1) ...
Setting up openclipart-libreoffice (0.18+dfsg-10ubuntu1) ...
Setting up openoffice.org-dtd-officedocument1.0 (2:1.0+LibO3.3.3-1ubuntu2) ...
Setting up uno-libs3-dbg (1.7.0+LibO3.3.3-1ubuntu2) ...
Setting up ure-dbg (1.7.0+LibO3.3.3-1ubuntu2) ...
Processing triggers for dictionaries-common ...
aspell-autobuildhash: processing: en [en-common]
aspell-autobuildhash: processing: en [en-variant_0]
aspell-autobuildhash: processing: en [en-variant_1]
aspell-autobuildhash: processing: en [en-variant_2]
aspell-autobuildhash: processing: en [en_CA-w_accents-only]
aspell-autobuildhash: processing: en [en_CA-wo_accents-only]
aspell-autobuildhash: processing: en [en_GB-ise-w_accents-only]
aspell-autobuildhash: processing: en [en_GB-ise-wo_accents-only]
aspell-autobuildhash: processing: en [en_GB-ize-w_accents-only]
aspell-autobuildhash: processing: en [en_GB-ize-wo_accents-only]
aspell-autobuildhash: processing: en [en_US-w_accents-only]
aspell-autobuildhash: processing: en [en_US-wo_accents-only]
Setting up aspell (0.60.6-6) ...
Processing triggers for dictionaries-common ...
Setting up aspell-en (6.0-0-6ubuntu1) ...
Processing triggers for dictionaries-common ...
Setting up libreoffice-core (1:3.3.3-1ubuntu2) ...
file:///usr/lib/libreoffice/basis3.3/program/libbf_migratefilterlx.so
register component 'file:///usr/lib/libreoffice/basis3.3/program/libbf_migratefilterlx.so' in registry '/var/lib/libreoffice/basis3.3/program/services.rdb' successful!
file:///usr/lib/libreoffice/basis3.3/program/libbindetlx.so
register component 'file:///usr/lib/libreoffice/basis3.3/program/libbindetlx.so' in registry '/var/lib/libreoffice/basis3.3/program/services.rdb' successful!
file:///usr/lib/libreoffice/basis3.3/program/libevoablx.so
register component 'file:///usr/lib/libreoffice/basis3.3/program/libevoablx.so' in registry '/var/lib/libreoffice/basis3.3/program/services.rdb' successful!
Setting up libreoffice-style-human (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-base-core (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-writer (1:3.3.3-1ubuntu2) ...
Setting up python-uno (1:3.3.3-1ubuntu2) ...
Setting up docvert-libreoffice (4.0-2) ...
Adding system user `docvert' (UID 114) ...
Adding new group `docvert' (GID 125) ...
Adding new user `docvert' (UID 114) with group `docvert' ...
Creating home directory `/var/lib/docvert/home' ...
 * Starting LibreOffice service for Docvert docvert-converter            [ OK ] 
Setting up libntrack0 (011-1ubuntu1.1) ...
Setting up ntrack-module-libnl-0 (011-1ubuntu1.1) ...
Setting up libntrack-qt4-1 (011-1ubuntu1.1) ...
Setting up kdebase-runtime (4:4.6.2-0ubuntu1) ...
update-alternatives: using /usr/lib/kde4/libexec/kdesu-distrib/kdesu to provide /usr/lib/kde4/libexec/kdesu (kdesu) in auto mode.
Setting up qapt-batch (1.1.2-0ubuntu1) ...
Setting up kubuntu-debug-installer (11.04ubuntu1) ...
Setting up libreoffice-calc (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-draw (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-impress (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-math (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-dev (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-emailmerge (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-filter-binfilter (1:3.3.3-1ubuntu2) ...
file:///usr/lib/libreoffice/basis3.3/program/libbf_migratefilterlx.so
register component 'file:///usr/lib/libreoffice/basis3.3/program/libbf_migratefilterlx.so' in registry '/var/lib/libreoffice/basis3.3/program/services.rdb' successful!
file:///usr/lib/libreoffice/basis3.3/program/libbindetlx.so
register component 'file:///usr/lib/libreoffice/basis3.3/program/libbindetlx.so' in registry '/var/lib/libreoffice/basis3.3/program/services.rdb' successful!
Setting up libreoffice-gtk (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-gnome (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-help-en-us (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-kde (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-mysql-connector (1.0.1+LibO3.3.3-1ubuntu2) ...
Setting up libreoffice-presentation-minimizer (1.0.3+LibO3.3.3-1ubuntu2) ...
Setting up libreoffice-presenter-console (1.1.0+LibO3.3.3-1ubuntu2) ...
Setting up libreoffice-sdbc-postgresql (1:0.7.6+LibO3.3.3-1ubuntu2) ...
Setting up libreoffice-voikko (3.2~rc2-1) ...
Setting up mozilla-libreoffice (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-dbg (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-nlpsolver (0.9~beta1-5) ...
Setting up libreoffice-pdfimport (1.0.3+LibO3.3.3-1ubuntu2) ...
Setting up libreoffice-style-hicontrast (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-style-galaxy (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-style-crystal (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-style-tango (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-style-oxygen (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-style-andromeda (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-common (1:3.3.3-1ubuntu2) ...
Synchronizing repository for shared extensions
 


 Synchronizing repository for bundled extensions
  


  Enabling: MySQL Connector
   Enabling: mysqlc.uno.so
   Enabling: Drivers.xcu
  Enabling: PDF Import
   Enabling: PDFImport
   Enabling: xpdfimport
   Enabling: pdfimport.uno.so
   Enabling: pdf_import_filter.xcu
   Enabling: pdf_types.xcu
  Enabling: Postgresql-SDBC Driver
   Enabling: postgresql-sdbc-impl.uno.so
   Enabling: postgresql-sdbc.uno.so
   Enabling: postgresql.xcu
  Enabling: Presentation Minimizer
   Enabling: SunPresentationMinimizer.xcs
   Enabling: SunPresentationMinimizer.uno.so
   Enabling: SunPresentationMinimizer.xcu
   Enabling: Addons.xcu
   Enabling: ProtocolHandler.xcu
  Enabling: Presenter Console
   Enabling: help
   Enabling: PresenterScreen.xcs
   Enabling: PresenterScreen.uno.so
   Enabling: Jobs.xcu
   Enabling: ProtocolHandler.xcu
   Enabling: PresenterScreen.xcu
  Enabling: Report Builder
   Enabling: ReportCommands.xcs
   Enabling: DbReportWindowState.xcs
   Enabling: ReportDesign.xcs
   Enabling: sun-report-builder.jar
   Enabling: Setup.xcu
   Enabling: DataAccess.xcu
   Enabling: ReportDesign.xcu
   Enabling: ExtendedColorScheme.xcu
   Enabling: Embedding.xcu
   Enabling: Paths.xcu
   Enabling: Accelerators.xcu
   Enabling: ReportCommands.xcu
   Enabling: Controller.xcu
   Enabling: DbReportWindowState.xcu
   Enabling: Filter.xcu
   Enabling: Types.xcu
  Enabling: Solver for Nonlinear Programming
   Enabling: help
   Enabling: NLPSolver.jar
  Enabling: Voikko - Finnish language tools
   Enabling: config.xcs
   Enabling: voikko.so
   Enabling: config.xcu
   Enabling: SettingsDialog.xcu
   Enabling: Linguistic.xcu
  Enabling: Wiki Publisher
   Enabling: help
   Enabling: WikiExtension.xcs
   Enabling: WikiEditor
   Enabling: mediawiki.jar
   Enabling: Addons.xcu
   Enabling: ProtocolHandler.xcu
   Enabling: WikiExtension.xcu
   Enabling: OptionsDialog.xcu
   Enabling: Filter.xcu
   Enabling: Types.xcu
   Enabling: Paths.xcu
  Enabling: Writer2LaTeX export filters
   Enabling: writer2latex.rdb
   Enabling: W2LDialogs
   Enabling: Options.xcs
   Enabling: writer2latex-filter.jar
   Enabling: w2l_types.xcu
   Enabling: w2l_filters.xcu
   Enabling: Options.xcu
  Enabling: Writer2xhtml export filters
   Enabling: writer2xhtml.rdb
   Enabling: W2XDialogs
   Enabling: Options.xcs
   Enabling: writer2xhtml-filter.jar
   Enabling: w2x_types.xcu
   Enabling: w2x_filters.xcu
   Enabling: Options.xcu

unopkg done.
Setting up libreoffice-java-common (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-base (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-report-builder-bin (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-report-builder (1:1.2.1+LibO3.3.3-1ubuntu2) ...
Setting up libreoffice-wiki-publisher (1.1.1+LibO3.3.3-1ubuntu2) ...
Setting up libreoffice-filter-mobiledev (1:3.3.3-1ubuntu2) ...
Setting up libreoffice (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-evolution (1:3.3.3-1ubuntu2) ...
file:///usr/lib/libreoffice/basis3.3/program/libevoablx.so
register component 'file:///usr/lib/libreoffice/basis3.3/program/libevoablx.so' in registry '/var/lib/libreoffice/basis3.3/program/services.rdb' successful!
Setting up libreoffice-gcj (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-l10n-ca (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-ca (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-cs (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-cs (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-da (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-da (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-de (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-de (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-dz (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-dz (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-el (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-el (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-en-gb (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-en-gb (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-es (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-es (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-et (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-et (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-eu (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-eu (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-fi (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-fi (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-fr (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-fr (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-gl (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-gl (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-hi (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-hi (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-hu (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-hu (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-it (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-it (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-ja (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-ja (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-km (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-km (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-ko (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-ko (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-nl (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-nl (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-om (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-om (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-pl (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-pl (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-pt (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-pt (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-pt-br (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-pt-br (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-ru (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-ru (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-sk (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-sk (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-sl (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-sl (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-sv (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-sv (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-zh-cn (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-zh-cn (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-zh-tw (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-help-zh-tw (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-af (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-ar (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-as (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-ast (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-be-by (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-bg (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-bn (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-br (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-bs (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-cy (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-en-za (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-eo (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-fa (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-ga (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-gu (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-he (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-hr (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-id (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-ml (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-mr (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-or (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-pa-in (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-ta (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-te (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-in (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-l10n-is (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-ka (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-ku (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-lt (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-lv (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-mk (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-mn (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-nb (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-ne (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-nn (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-nr (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-ns (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-oc (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-ro (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-rw (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-si (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-sr (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-ss (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-st (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-tg (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-th (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-tn (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-tr (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-ts (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-ug (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-uk (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-uz (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-ve (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-vi (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-xh (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-zu (1:3.3.3-1ubuntu1) ...
Setting up libreoffice-l10n-za (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-officebean (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-writer2latex (1.0.2-3ubuntu1) ...
Setting up libreoffice-writer2xhtml (1.0.2-3ubuntu1) ...
Setting up libreoffice-ogltrans (1:3.3.3-1ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```if I start libreoffice now, I got NO error message. 
But it starts not. 

I think the Korean/Japanes Whatever text is: 

A general error occurred while accessing your central configuration

(I had this message before in english)

---

### Post by jdb on 2011-08-20
[QUOTE=flo1805;11170521]so now i did the following:

```
sudo rm -rf .libreoffice* && sudo apt-get purge libreoffice* && sudo apt-get install libreoffice*
```

The *'s are good for the rm and the purge,
but the * on the install is causing problems.

An * is a wild card which is causing every package that starts
with the name libreoffice to be installed.
That's where the Asian language characters came from.

Try the same script again, use the *'s on the rm and purge just
like before to get rid of all the junk that got installed but do
NOT put an * after libreoffice on the install command.

Installing libreoffice by itself will trigger any other required
packages to be installed automatically, they are "dependencies".

I don't know if this will fix the original problem or not, but in might be worth a try.

jdb

---

### Post by flo1805 on 2011-08-20
ok. I did

```
sudo rm -rfv .libreoffice* && sudo apt-get purge libreoffice* && sudo apt-get install libreoffice
```and now I get the first error message again

```
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'

```I always have thes dpkg warning while removing libreoffice.

```

dpkg: warning: while removing libreoffice-common, directory '/var/lib/libreoffice/share/prereg/bundled' not empty so not removed.
dpkg: warning: while removing libreoffice-common, directory '/var/lib/libreoffice/share/prereg' not empty so not removed.
dpkg: warning: while removing libreoffice-common, directory '/var/lib/libreoffice/share' not empty so not removed.
dpkg: warning: while removing libreoffice-common, directory '/var/spool/libreoffice/uno_packages/cache' not empty so not removed.
dpkg: warning: while removing libreoffice-common, directory '/var/spool/libreoffice/uno_packages' not empty so not removed.
dpkg: warning: while removing libreoffice-common, directory '/var/spool/libreoffice' not empty so not removed.

```could this be a reason for the problem maybe? 
maybe the rights are false here?? (and if it will not be removed, they are also false, when I reinstall libreoffice)

```

florian@system:~$ ls -alR /var/lib/libreoffice/
/var/lib/libreoffice/:
total 16
drwxr-xr-x  4 root root 4096 2011-08-21 00:56 .
drwxr-xr-x 68 root root 4096 2011-08-20 19:44 ..
drwxr-xr-x  4 root root 4096 2011-08-21 00:56 basis3.3
drwxr-xr-x  3 root root 4096 2011-08-20 19:43 share

/var/lib/libreoffice/basis3.3:
total 16
drwxr-xr-x 4 root root 4096 2011-08-21 00:56 .
drwxr-xr-x 4 root root 4096 2011-08-21 00:56 ..
drwxr-xr-x 2 root root 4096 2011-08-21 00:56 program
drwxr-xr-x 3 root root 4096 2011-08-21 00:56 share

/var/lib/libreoffice/basis3.3/program:
total 5460
drwxr-xr-x 2 root root    4096 2011-08-21 00:56 .
drwxr-xr-x 4 root root    4096 2011-08-21 00:56 ..
-rw-r--r-- 1 root root 5581824 2011-07-21 17:36 services.rdb

/var/lib/libreoffice/basis3.3/share:
total 12
drwxr-xr-x 3 root root 4096 2011-08-21 00:56 .
drwxr-xr-x 4 root root 4096 2011-08-21 00:56 ..
drwxr-xr-x 2 root root 4096 2011-08-21 00:56 config

/var/lib/libreoffice/basis3.3/share/config:
total 12
drwxr-xr-x 2 root root 4096 2011-08-21 00:56 .
drwxr-xr-x 3 root root 4096 2011-08-21 00:56 ..
-rw-r--r-- 1 root root 1570 2011-08-21 00:56 javasettingsunopkginstall.xml

/var/lib/libreoffice/share:
total 12
drwxr-xr-x 3 root root 4096 2011-08-20 19:43 .
drwxr-xr-x 4 root root 4096 2011-08-21 00:56 ..
drwxr-xr-x 3 root root 4096 2011-08-20 19:43 prereg

/var/lib/libreoffice/share/prereg:
total 12
drwxr-xr-x 3 root root 4096 2011-08-20 19:43 .
drwxr-xr-x 3 root root 4096 2011-08-20 19:43 ..
drwxr-xr-x 2 root root 4096 2011-08-21 00:56 bundled

/var/lib/libreoffice/share/prereg/bundled:
total 8
drwxr-xr-x 2 root root 4096 2011-08-21 00:56 .
drwxr-xr-x 3 root root 4096 2011-08-20 19:43 ..


```

```

florian@system:~$ ls -alR /var/spool/libreoffice/
/var/spool/libreoffice/:
total 12
drwxr-xr-x 3 root root 4096 2011-08-21 00:56 .
drwxr-xr-x 9 root root 4096 2011-08-21 00:56 ..
drwxr-xr-x 3 root root 4096 2011-08-21 00:56 uno_packages

/var/spool/libreoffice/uno_packages:
total 12
drwxr-xr-x 3 root root 4096 2011-08-21 00:56 .
drwxr-xr-x 3 root root 4096 2011-08-21 00:56 ..
drwxr-xr-x 2 root root 4096 2011-07-21 18:14 cache

/var/spool/libreoffice/uno_packages/cache:
total 8
drwxr-xr-x 2 root root 4096 2011-07-21 18:14 .
drwxr-xr-x 3 root root 4096 2011-08-21 00:56 ..

```


what a sick problem...
:mad:


btw full code (maybe ist usefull)

```

florian@system:~$ sudo rm -vrf .libreoffice* &&  sudo apt-get purge libreoffice* && sudo apt-get install libreoffice
[sudo] password for florian: 
removed `.libreoffice/3/user/config/javasettings_Linux_X86_64.xml'
removed directory: `.libreoffice/3/user/config'
removed `.libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/backenddb.xml'
removed directory: `.libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/extensions/bundled/registry'
removed directory: `.libreoffice/3/user/extensions/bundled'
removed directory: `.libreoffice/3/user/extensions'
removed directory: `.libreoffice/3/user'
removed directory: `.libreoffice/3'
removed directory: `.libreoffice'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libreoffice-writer' for regex 'libreoffice*'
Note, selecting 'libreoffice-calc' for regex 'libreoffice*'
Note, selecting 'libreoffice-impress' for regex 'libreoffice*'
Note, selecting 'libreoffice-kde' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-oxygen' for regex 'libreoffice*'
Note, selecting 'libreoffice-base' for regex 'libreoffice*'
Note, selecting 'libreoffice-core' for regex 'libreoffice*'
Note, selecting 'libreoffice-base-core' for regex 'libreoffice*'
Note, selecting 'libreoffice-java-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-gcj' for regex 'libreoffice*'
Note, selecting 'libreoffice-report-builder' for regex 'libreoffice*'
Note, selecting 'libreoffice-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-default' for regex 'libreoffice*'
Note, selecting 'libreoffice-style' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-hicontrast' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-tango' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-crystal' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-human' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-andromeda' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-galaxy' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-industrial' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-us' for regex 'libreoffice*'
Note, selecting 'libreoffice-dev' for regex 'libreoffice*'
Note, selecting 'libreoffice-draw' for regex 'libreoffice*'
Note, selecting 'libreoffice-evolution' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-so52' for regex 'libreoffice*'
Note, selecting 'libreoffice-gnome' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk' for regex 'libreoffice*'
Note, selecting 'libreoffice-officebean' for regex 'libreoffice*'
Note, selecting 'libreoffice-bundled' for regex 'libreoffice*'
Note, selecting 'libreoffice-dbg' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-binfilter' for regex 'libreoffice*'
Note, selecting 'mozilla-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-ogltrans' for regex 'libreoffice*'
Note, selecting 'libreoffice-dev-doc' for regex 'libreoffice*'
Note, selecting 'libreoffice-dtd-officedocument1.0' for regex 'libreoffice*'
Note, selecting 'libreoffice-emailmerge' for regex 'libreoffice*'
Note, selecting 'libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk-gnome' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-3.3.2' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-gb' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-gb' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-us' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pt-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pt-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sv' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sv' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zh-tw' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zh-tw' for regex 'libreoffice*'
Note, selecting 'libreoffice-kab' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-3.3.2' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ast' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ast' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-be-by' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-be-by' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-ctl-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-or' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ta' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-te' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ku' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ku' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ns' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ns' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-or' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-rw' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-rw' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-si' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-si' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ss' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ss' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-st' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-st' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ta' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-te' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tg' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tg' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-th' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-th' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ts' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ts' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ug' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ug' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-uk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-uk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-uz' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-uz' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ve' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ve' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-vi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-vi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-xh' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-xh' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zu' for regex 'libreoffice*'
Note, selecting 'libreoffice-math' for regex 'libreoffice*'
Note, selecting 'libreoffice-nlpsolver' for regex 'libreoffice*'
Note, selecting 'libreoffice-voikko' for regex 'libreoffice*'
Note, selecting 'libreoffice-hyphenation-fi' for regex 'libreoffice*'
Note, selecting 'docvert-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-report-builder-bin' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-mobiledev' for regex 'libreoffice*'
Note, selecting 'openclipart-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-mysql-connector' for regex 'libreoffice*'
Note, selecting 'libreoffice-pdfimport' for regex 'libreoffice*'
Note, selecting 'libreoffice-presentation-minimizer' for regex 'libreoffice*'
Note, selecting 'libreoffice-presenter-console' for regex 'libreoffice*'
Note, selecting 'libreoffice-reportdesigner' for regex 'libreoffice*'
Note, selecting 'libreoffice-sdbc-postgresql' for regex 'libreoffice*'
Note, selecting 'libreoffice-wiki-publisher' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer2latex' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer2xhtml' for regex 'libreoffice*'
Note, selecting 'libreoffice-dmaths' for regex 'libreoffice*'
Note, selecting 'libreoffice-zemberek' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-3.3.3' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-3.3.3' for regex 'libreoffice*'
Note, selecting 'libreoffice3.3-mandriva-menus' for regex 'libreoffice*'
Note, selecting 'libreoffice3.3-redhat-menus' for regex 'libreoffice*'
Note, selecting 'libreoffice3.3-suse-menus' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-human' instead of 'libreoffice-style-default'
Note, selecting 'libreoffice-common' instead of 'libreoffice-l10n-en-us'
Note, selecting 'libreoffice-core' instead of 'libreoffice-bundled'
Note, selecting 'openoffice.org-dtd-officedocument1.0' instead of 'libreoffice-dtd-officedocument1.0'
Note, selecting 'libreoffice-gnome' instead of 'libreoffice-gtk-gnome'
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-spellcheck-fi'
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-hyphenation-fi'
Note, selecting 'libreoffice-report-builder' instead of 'libreoffice-reportdesigner'
The following packages were automatically installed and are no longer required:
  kubuntu-debug-installer libdbusmenu-qt2 qapt-batch pwgen virtuoso-minimal
  libqca2 docvert libqt4-declarative libbase-java-openoffice.org
  ttf-dejavu-extra libpolkit-qt-1-1 libgcj-bc pdf2svg libknewstuff3-4
  libqapt-runtime php5-xsl libvirtodbc0 libmysqlcppconn4 libnepomukquery4a
  libqt4-script libqt4-network libqt4-dbus bsh-gcj libsac-java-gcj
  libthreadweaver4 libkdecore5 phonon libnepomukutils4 libktexteditor4
  ttf-indic-fonts voikko-fi libkmediaplayer4 ttf-sil-gentium docbook-xsl
  oxygen-icon-theme plasma-scriptengine-javascript libapr1
  libflute-java-openoffice.org libkrosscore4 libhsqldb-java gcj-jre
  ttf-dzongkha libapache2-mod-php5 libloader-java-openoffice.org
  libcommons-logging-java libaprutil1-ldap php5-tidy apache2-mpm-prefork
  ttf-devanagari-fonts php5-gd virtuoso-opensource-6.1-bin libqt4-opengl
  libmysqlclient16 apache2-utils libgcj11 libsolid4 ttf-khmeros librsvg2-bin
  libqt4-xmlpatterns libhsqldb-java-gcj libnepomuk4 ttf-gujarati-fonts
  appmenu-qt ure-dbg libsoprano4 ttf-arabeyes jpegoptim
  libformula-java-openoffice.org virtuoso-opensource-6.1-common
  ttf-telugu-fonts libkdnssd4 libkparts4 apache2.2-common
  plasma-scriptengine-declarative libclucene0ldbl
  libserializer-java-openoffice.org bsh libqapt1 shared-desktop-ontologies
  fckeditor ttf-bengali-fonts kdoctools libqtcore4 libgif4 libsac-java
  libreadline5 libaprutil1-dbd-sqlite3 culmus gcj-4.5-jre-headless
  apache2.2-bin icoutils libkidletime4 gcj-4.5-base libkcmutils4
  ttf-malayalam-fonts libntrack0 soprano-daemon libqt4-sql libkfile4
  libqt4-svg libservlet2.5-java libkpty4 ttf-sil-gentium-basic
  libcommons-httpclient-java gcj-jre-headless gcj-4.5-jre-lib libphonon4
  libpentaho-reporting-flow-engine-java-openoffice.org ttf-tamil-fonts
  libqt4-xml libkntlm4 ttf-farsiweb libplasma3 ttf-dejavu libphp-pclzip
  phonon-backend-gstreamer libkemoticons4 ntrack-module-libnl-0 kdelibs-bin
  libgcj11-awt libkdewebkit5 libqtgui4 libattica0 dmake libkjsembed4 libkio5
  libpq5 libkjsapi4 libstreams0 libcommons-codec-java libcommons-lang-java
  openclipart-png libntrack-qt4-1 libvoikko1 ttf-kannada-fonts kdelibs5-data
  kdebase-runtime gcj-4.5-jre libgcj-common libqt4-sql-mysql php5-cli
  libqtwebkit4 uno-libs3-dbg libssh-4 libaudio2 libknotifyconfig4
  liblayout-java-openoffice.org kdebase-runtime-data libaprutil1
  ttf-oriya-fonts kdelibs5-plugins libiodbc2 libkhtml5 libkdeui5 mysql-common
  php5-common libjline-java libkdesu5 librepository-java-openoffice.org
  libkatepartinterfaces4 optipng libxml-java-openoffice.org libtidy-0.99-0
  libfonts-java-openoffice.org libstreamanalyzer0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  docvert-libreoffice* libreoffice* libreoffice-base* libreoffice-base-core*
  libreoffice-calc* libreoffice-common* libreoffice-core* libreoffice-dbg*
  libreoffice-dev* libreoffice-dev-doc* libreoffice-draw*
  libreoffice-emailmerge* libreoffice-evolution* libreoffice-filter-binfilter*
  libreoffice-filter-mobiledev* libreoffice-gcj* libreoffice-gnome*
  libreoffice-gtk* libreoffice-help-ca* libreoffice-help-cs*
  libreoffice-help-da* libreoffice-help-de* libreoffice-help-dz*
  libreoffice-help-el* libreoffice-help-en-gb* libreoffice-help-en-us*
  libreoffice-help-es* libreoffice-help-et* libreoffice-help-eu*
  libreoffice-help-fi* libreoffice-help-fr* libreoffice-help-gl*
  libreoffice-help-hi* libreoffice-help-hu* libreoffice-help-it*
  libreoffice-help-ja* libreoffice-help-km* libreoffice-help-ko*
  libreoffice-help-nl* libreoffice-help-om* libreoffice-help-pl*
  libreoffice-help-pt* libreoffice-help-pt-br* libreoffice-help-ru*
  libreoffice-help-sk* libreoffice-help-sl* libreoffice-help-sv*
  libreoffice-help-zh-cn* libreoffice-help-zh-tw* libreoffice-impress*
  libreoffice-java-common* libreoffice-kde* libreoffice-l10n-af*
  libreoffice-l10n-ar* libreoffice-l10n-as* libreoffice-l10n-ast*
  libreoffice-l10n-be-by* libreoffice-l10n-bg* libreoffice-l10n-bn*
  libreoffice-l10n-br* libreoffice-l10n-bs* libreoffice-l10n-ca*
  libreoffice-l10n-common* libreoffice-l10n-cs* libreoffice-l10n-cy*
  libreoffice-l10n-da* libreoffice-l10n-de* libreoffice-l10n-dz*
  libreoffice-l10n-el* libreoffice-l10n-en-gb* libreoffice-l10n-en-za*
  libreoffice-l10n-eo* libreoffice-l10n-es* libreoffice-l10n-et*
  libreoffice-l10n-eu* libreoffice-l10n-fa* libreoffice-l10n-fi*
  libreoffice-l10n-fr* libreoffice-l10n-ga* libreoffice-l10n-gl*
  libreoffice-l10n-gu* libreoffice-l10n-he* libreoffice-l10n-hi*
  libreoffice-l10n-hr* libreoffice-l10n-hu* libreoffice-l10n-id*
  libreoffice-l10n-in* libreoffice-l10n-is* libreoffice-l10n-it*
  libreoffice-l10n-ja* libreoffice-l10n-ka* libreoffice-l10n-km*
  libreoffice-l10n-ko* libreoffice-l10n-ku* libreoffice-l10n-lt*
  libreoffice-l10n-lv* libreoffice-l10n-mk* libreoffice-l10n-ml*
  libreoffice-l10n-mn* libreoffice-l10n-mr* libreoffice-l10n-nb*
  libreoffice-l10n-ne* libreoffice-l10n-nl* libreoffice-l10n-nn*
  libreoffice-l10n-nr* libreoffice-l10n-ns* libreoffice-l10n-oc*
  libreoffice-l10n-om* libreoffice-l10n-or* libreoffice-l10n-pa-in*
  libreoffice-l10n-pl* libreoffice-l10n-pt* libreoffice-l10n-pt-br*
  libreoffice-l10n-ro* libreoffice-l10n-ru* libreoffice-l10n-rw*
  libreoffice-l10n-si* libreoffice-l10n-sk* libreoffice-l10n-sl*
  libreoffice-l10n-sr* libreoffice-l10n-ss* libreoffice-l10n-st*
  libreoffice-l10n-sv* libreoffice-l10n-ta* libreoffice-l10n-te*
  libreoffice-l10n-tg* libreoffice-l10n-th* libreoffice-l10n-tn*
  libreoffice-l10n-tr* libreoffice-l10n-ts* libreoffice-l10n-ug*
  libreoffice-l10n-uk* libreoffice-l10n-uz* libreoffice-l10n-ve*
  libreoffice-l10n-vi* libreoffice-l10n-xh* libreoffice-l10n-za*
  libreoffice-l10n-zh-cn* libreoffice-l10n-zh-tw* libreoffice-l10n-zu*
  libreoffice-math* libreoffice-mysql-connector* libreoffice-nlpsolver*
  libreoffice-officebean* libreoffice-ogltrans* libreoffice-pdfimport*
  libreoffice-presentation-minimizer* libreoffice-presenter-console*
  libreoffice-report-builder* libreoffice-report-builder-bin*
  libreoffice-sdbc-postgresql* libreoffice-style-andromeda*
  libreoffice-style-crystal* libreoffice-style-galaxy*
  libreoffice-style-hicontrast* libreoffice-style-human*
  libreoffice-style-oxygen* libreoffice-style-tango* libreoffice-voikko*
  libreoffice-wiki-publisher* libreoffice-writer* libreoffice-writer2latex*
  libreoffice-writer2xhtml* mozilla-libreoffice* openclipart-libreoffice*
  openoffice.org-dtd-officedocument1.0* python-uno*
0 upgraded, 0 newly installed, 167 to remove and 0 not upgraded.
After this operation, 1,884 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 247780 files and directories currently installed.)
Removing docvert-libreoffice ...
 * Stopping LibreOffice service for Docvert docvert-converter            [ OK ] 
Removing user `docvert' ...
Warning: group `docvert' has no more members.
Done.
Purging configuration files for docvert-libreoffice ...
/usr/sbin/deluser: The user `docvert' does not exist.
Removing libreoffice ...
Removing libreoffice-report-builder ...
Removing libreoffice-report-builder-bin ...
Removing libreoffice-evolution ...
file:///usr/lib/libreoffice/basis3.3/program/libevoablx.so
revoke component 'file:///usr/lib/libreoffice/basis3.3/program/libevoablx.so' from registry '/var/lib/libreoffice/basis3.3/program/services.rdb' successful!
Removing libreoffice-dbg ...
Removing libreoffice-base ...
Purging configuration files for libreoffice-base ...
Removing libreoffice-help-zh-tw ...
Removing libreoffice-help-zh-cn ...
Removing libreoffice-help-sv ...
Removing libreoffice-help-sl ...
Removing libreoffice-help-sk ...
Removing libreoffice-help-ru ...
Removing libreoffice-help-pt-br ...
Removing libreoffice-help-pt ...
Removing libreoffice-help-pl ...
Removing libreoffice-help-om ...
Removing libreoffice-help-nl ...
Removing libreoffice-help-ko ...
Removing libreoffice-help-km ...
Removing libreoffice-help-ja ...
Removing libreoffice-help-it ...
Removing libreoffice-help-hu ...
Removing libreoffice-help-hi ...
Removing libreoffice-help-gl ...
Removing libreoffice-help-fr ...
Removing libreoffice-help-fi ...
Removing libreoffice-help-eu ...
Removing libreoffice-help-et ...
Removing libreoffice-help-es ...
Removing libreoffice-help-en-us ...
Removing libreoffice-help-en-gb ...
Removing libreoffice-help-el ...
Removing libreoffice-help-dz ...
Removing libreoffice-help-de ...
Removing libreoffice-help-da ...
Removing libreoffice-help-cs ...
Removing libreoffice-help-ca ...
Removing libreoffice-writer ...
Purging configuration files for libreoffice-writer ...
Removing libreoffice-nlpsolver ...
Removing libreoffice-calc ...
Purging configuration files for libreoffice-calc ...
Removing libreoffice-base-core ...
Removing libreoffice-ogltrans ...
Removing libreoffice-l10n-za ...
Removing libreoffice-l10n-zu ...
Removing libreoffice-l10n-zh-tw ...
Removing libreoffice-l10n-zh-cn ...
Removing libreoffice-l10n-xh ...
Removing libreoffice-l10n-vi ...
Removing libreoffice-l10n-ve ...
Removing libreoffice-l10n-uz ...
Removing libreoffice-l10n-uk ...
Removing libreoffice-l10n-ug ...
Removing libreoffice-l10n-ts ...
Removing libreoffice-l10n-tr ...
Removing libreoffice-l10n-tn ...
Removing libreoffice-l10n-th ...
Removing libreoffice-l10n-tg ...
Removing libreoffice-l10n-in ...
Removing libreoffice-l10n-te ...
Removing libreoffice-l10n-ta ...
Removing libreoffice-l10n-sv ...
Removing libreoffice-l10n-st ...
Removing libreoffice-l10n-ss ...
Removing libreoffice-l10n-sr ...
Removing libreoffice-l10n-sl ...
Removing libreoffice-l10n-sk ...
Removing libreoffice-l10n-si ...
Removing libreoffice-l10n-rw ...
Removing libreoffice-l10n-ru ...
Removing libreoffice-l10n-ro ...
Removing libreoffice-l10n-pt-br ...
Removing libreoffice-l10n-pt ...
Removing libreoffice-l10n-pl ...
Removing libreoffice-l10n-pa-in ...
Removing libreoffice-l10n-or ...
Removing libreoffice-l10n-om ...
Removing libreoffice-l10n-oc ...
Removing libreoffice-l10n-ns ...
Removing libreoffice-l10n-nr ...
Removing libreoffice-l10n-nn ...
Removing libreoffice-l10n-nl ...
Removing libreoffice-l10n-ne ...
Removing libreoffice-l10n-nb ...
Removing libreoffice-l10n-mr ...
Removing libreoffice-l10n-mn ...
Removing libreoffice-l10n-ml ...
Removing libreoffice-l10n-mk ...
Removing libreoffice-l10n-lv ...
Removing libreoffice-l10n-lt ...
Removing libreoffice-l10n-ku ...
Removing libreoffice-l10n-ko ...
Removing libreoffice-l10n-km ...
Removing libreoffice-l10n-ka ...
Removing libreoffice-l10n-ja ...
Removing libreoffice-l10n-it ...
Removing libreoffice-l10n-is ...
Removing libreoffice-l10n-id ...
Removing libreoffice-l10n-hu ...
Removing libreoffice-l10n-hr ...
Removing libreoffice-l10n-hi ...
Removing libreoffice-l10n-he ...
Removing libreoffice-l10n-gu ...
Removing libreoffice-l10n-gl ...
Removing libreoffice-l10n-ga ...
Removing libreoffice-l10n-fr ...
Removing libreoffice-l10n-fi ...
Removing libreoffice-l10n-fa ...
Removing libreoffice-l10n-eu ...
Removing libreoffice-l10n-et ...
Removing libreoffice-l10n-es ...
Removing libreoffice-l10n-eo ...
Removing libreoffice-l10n-en-za ...
Removing libreoffice-l10n-en-gb ...
Removing libreoffice-l10n-el ...
Removing libreoffice-l10n-dz ...
Removing libreoffice-l10n-de ...
Removing libreoffice-l10n-da ...
Removing libreoffice-l10n-cy ...
Removing libreoffice-l10n-cs ...
Removing libreoffice-l10n-ca ...
Removing libreoffice-l10n-bs ...
Removing libreoffice-l10n-br ...
Removing libreoffice-l10n-bn ...
Removing libreoffice-l10n-bg ...
Removing libreoffice-l10n-be-by ...
Removing libreoffice-l10n-ast ...
Removing libreoffice-l10n-as ...
Removing libreoffice-l10n-ar ...
Removing libreoffice-l10n-af ...
Removing libreoffice-wiki-publisher ...
Removing libreoffice-filter-mobiledev ...
Removing libreoffice-officebean ...
Removing libreoffice-gcj ...
Purging configuration files for libreoffice-gcj ...
Removing libreoffice-writer2xhtml ...
Removing libreoffice-writer2latex ...
Removing libreoffice-java-common ...
Removing mozilla-libreoffice ...
Removing libreoffice-style-hicontrast ...
Removing libreoffice-style-galaxy ...
Removing libreoffice-style-crystal ...
Removing libreoffice-sdbc-postgresql ...
Removing libreoffice-presenter-console ...
Removing libreoffice-presentation-minimizer ...
Removing libreoffice-pdfimport ...
Removing libreoffice-mysql-connector ...
Removing libreoffice-emailmerge ...
Removing python-uno ...
Removing libreoffice-style-tango ...
Removing libreoffice-style-oxygen ...
Removing libreoffice-style-andromeda ...
Removing libreoffice-math ...
Purging configuration files for libreoffice-math ...
Removing libreoffice-kde ...
Removing libreoffice-impress ...
Purging configuration files for libreoffice-impress ...
Removing libreoffice-gnome ...
Removing libreoffice-gtk ...
Removing libreoffice-filter-binfilter ...
file:///usr/lib/libreoffice/basis3.3/program/libbf_migratefilterlx.so
revoke component 'file:///usr/lib/libreoffice/basis3.3/program/libbf_migratefilterlx.so' from registry '/var/lib/libreoffice/basis3.3/program/services.rdb' successful!
file:///usr/lib/libreoffice/basis3.3/program/libbindetlx.so
revoke component 'file:///usr/lib/libreoffice/basis3.3/program/libbindetlx.so' from registry '/var/lib/libreoffice/basis3.3/program/services.rdb' successful!
Purging configuration files for libreoffice-filter-binfilter ...
Removing libreoffice-draw ...
Purging configuration files for libreoffice-draw ...
Removing libreoffice-dev ...
Removing libreoffice-voikko ...
Removing libreoffice-dev-doc ...
Removing libreoffice-l10n-common ...
Removing openclipart-libreoffice ...
Removing openoffice.org-dtd-officedocument1.0 ...
Purging configuration files for openoffice.org-dtd-officedocument1.0 ...
Removing libreoffice-common ...
Purging configuration files for libreoffice-common ...
dpkg: warning: while removing libreoffice-common, directory '/var/lib/libreoffice/share/prereg/bundled' not empty so not removed.
dpkg: warning: while removing libreoffice-common, directory '/var/lib/libreoffice/share/prereg' not empty so not removed.
dpkg: warning: while removing libreoffice-common, directory '/var/lib/libreoffice/share' not empty so not removed.
dpkg: warning: while removing libreoffice-common, directory '/var/spool/libreoffice/uno_packages/cache' not empty so not removed.
dpkg: warning: while removing libreoffice-common, directory '/var/spool/libreoffice/uno_packages' not empty so not removed.
dpkg: warning: while removing libreoffice-common, directory '/var/spool/libreoffice' not empty so not removed.
Removing libreoffice-style-human ...
Removing libreoffice-core ...
Purging configuration files for libreoffice-core ...
dpkg: warning: while removing libreoffice-core, directory '/var/lib/libreoffice' not empty so not removed.
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for doc-base ...
Processing 3 removed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kubuntu-debug-installer libdbusmenu-qt2 qapt-batch pwgen virtuoso-minimal
  libqca2 docvert libqt4-declarative libbase-java-openoffice.org
  libpolkit-qt-1-1 libgcj-bc pdf2svg libknewstuff3-4 libqapt-runtime php5-xsl
  libvirtodbc0 libmysqlcppconn4 libnepomukquery4a libqt4-script libqt4-network
  libqt4-dbus bsh-gcj libsac-java-gcj libthreadweaver4 libkdecore5 phonon
  libnepomukutils4 libktexteditor4 ttf-indic-fonts voikko-fi libkmediaplayer4
  docbook-xsl oxygen-icon-theme plasma-scriptengine-javascript libapr1
  libflute-java-openoffice.org libkrosscore4 ttf-dzongkha libapache2-mod-php5
  libloader-java-openoffice.org libcommons-logging-java libaprutil1-ldap
  php5-tidy apache2-mpm-prefork ttf-devanagari-fonts php5-gd
  virtuoso-opensource-6.1-bin libqt4-opengl libmysqlclient16 apache2-utils
  libsolid4 ttf-khmeros librsvg2-bin libqt4-xmlpatterns libhsqldb-java-gcj
  libnepomuk4 ttf-gujarati-fonts appmenu-qt ure-dbg libsoprano4 ttf-arabeyes
  jpegoptim libformula-java-openoffice.org virtuoso-opensource-6.1-common
  ttf-telugu-fonts libkdnssd4 libkparts4 apache2.2-common
  plasma-scriptengine-declarative libclucene0ldbl
  libserializer-java-openoffice.org bsh libqapt1 shared-desktop-ontologies
  fckeditor ttf-bengali-fonts kdoctools libqtcore4 libgif4 libsac-java
  libreadline5 libaprutil1-dbd-sqlite3 culmus apache2.2-bin icoutils
  libkidletime4 libkcmutils4 ttf-malayalam-fonts libntrack0 soprano-daemon
  libqt4-sql libkfile4 libqt4-svg libkpty4 libcommons-httpclient-java
  libphonon4 libpentaho-reporting-flow-engine-java-openoffice.org
  ttf-tamil-fonts libqt4-xml libkntlm4 ttf-farsiweb libplasma3 libphp-pclzip
  phonon-backend-gstreamer libkemoticons4 ntrack-module-libnl-0 kdelibs-bin
  libkdewebkit5 libqtgui4 libattica0 dmake libkjsembed4 libkio5 libpq5
  libkjsapi4 libstreams0 libcommons-codec-java libcommons-lang-java
  openclipart-png libntrack-qt4-1 libvoikko1 ttf-kannada-fonts kdelibs5-data
  kdebase-runtime libqt4-sql-mysql php5-cli libqtwebkit4 uno-libs3-dbg
  libssh-4 libaudio2 libknotifyconfig4 liblayout-java-openoffice.org
  kdebase-runtime-data libaprutil1 ttf-oriya-fonts kdelibs5-plugins libiodbc2
  libkhtml5 libkdeui5 mysql-common php5-common libjline-java libkdesu5
  librepository-java-openoffice.org libkatepartinterfaces4 optipng
  libxml-java-openoffice.org libtidy-0.99-0 libfonts-java-openoffice.org
  libstreamanalyzer0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-base libreoffice-base-core libreoffice-calc libreoffice-common
  libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-filter-mobiledev libreoffice-impress libreoffice-java-common
  libreoffice-math libreoffice-report-builder-bin libreoffice-style-human
  libreoffice-writer python-uno
Suggested packages:
  hunspell-dictionary myspell-dictionary libreoffice-help-3.3.3 menu
  hyphen-hyphenation-patterns mythes-thesaurus libreoffice-gnome
  libreoffice-kde openclipart-libreoffice pstoedit imagemagick
  graphicsmagick-imagemagick-compat libreoffice-filter-binfilter
  libreoffice-officebean libmyodbc odbc-postgresql libsqliteodbc tdsodbc
  mdbtools libmysql-java libpg-java libjtds-java libreoffice-gcj
  libreoffice-report-builder libreoffice-style-hicontrast
  libreoffice-style-tango libreoffice-style-crystal libreoffice-style-oxygen
  kde-icons-crystal crystalcursors
The following NEW packages will be installed:
  libreoffice libreoffice-base libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-filter-mobiledev libreoffice-impress libreoffice-java-common
  libreoffice-math libreoffice-report-builder-bin libreoffice-style-human
  libreoffice-writer python-uno
0 upgraded, 16 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/69.5 MB of archives.
After this operation, 261 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libreoffice-style-human.
(Reading database ... 208435 files and directories currently installed.)
Unpacking libreoffice-style-human (from .../libreoffice-style-human_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-common.
Unpacking libreoffice-common (from .../libreoffice-common_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-core.
Unpacking libreoffice-core (from .../libreoffice-core_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-base-core.
Unpacking libreoffice-base-core (from .../libreoffice-base-core_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-writer.
Unpacking libreoffice-writer (from .../libreoffice-writer_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-calc.
Unpacking libreoffice-calc (from .../libreoffice-calc_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-draw.
Unpacking libreoffice-draw (from .../libreoffice-draw_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-impress.
Unpacking libreoffice-impress (from .../libreoffice-impress_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-math.
Unpacking libreoffice-math (from .../libreoffice-math_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-java-common.
Unpacking libreoffice-java-common (from .../libreoffice-java-common_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-base.
Unpacking libreoffice-base (from .../libreoffice-base_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-report-builder-bin.
Unpacking libreoffice-report-builder-bin (from .../libreoffice-report-builder-bin_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-filter-mobiledev.
Unpacking libreoffice-filter-mobiledev (from .../libreoffice-filter-mobiledev_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice.
Unpacking libreoffice (from .../libreoffice_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package python-uno.
Unpacking python-uno (from .../python-uno_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-emailmerge.
Unpacking libreoffice-emailmerge (from .../libreoffice-emailmerge_1%3a3.3.3-1ubuntu2_all.deb) ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for python-support ...
Setting up libreoffice-core (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-style-human (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-base-core (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-writer (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-calc (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-draw (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-impress (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-math (1:3.3.3-1ubuntu2) ...
Setting up python-uno (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-emailmerge (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-common (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-java-common (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-base (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-report-builder-bin (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-filter-mobiledev (1:3.3.3-1ubuntu2) ...
Setting up libreoffice (1:3.3.3-1ubuntu2) ...

```

---

### Post by jdb on 2011-08-20
Those files it can't delete may be the problem.
Here is what I got:
sudo rm -rfv .libreoffice* | tee rm.txt
```
removed `.libreoffice/3/user/basic/Standard/Module1.xba'
removed `.libreoffice/3/user/basic/Standard/dialog.xlb'
removed `.libreoffice/3/user/basic/Standard/script.xlb'
removed directory: `.libreoffice/3/user/basic/Standard'
removed `.libreoffice/3/user/basic/dialog.xlc'
removed `.libreoffice/3/user/basic/script.xlc'
removed directory: `.libreoffice/3/user/basic'
removed directory: `.libreoffice/3/user/uno_packages/cache/uno_packages'
removed `.libreoffice/3/user/uno_packages/cache/uno_packages.db'
removed directory: `.libreoffice/3/user/uno_packages/cache/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend'
removed `.libreoffice/3/user/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registered_packages.db'
removed `.libreoffice/3/user/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/backenddb.xml'
removed directory: `.libreoffice/3/user/uno_packages/cache/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/uno_packages/cache/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/uno_packages/cache/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend'
removed `.libreoffice/3/user/uno_packages/cache/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/backenddb.xml'
removed directory: `.libreoffice/3/user/uno_packages/cache/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/uno_packages/cache/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/uno_packages/cache/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/uno_packages/cache/registry'
removed `.libreoffice/3/user/uno_packages/cache/log.txt'
removed directory: `.libreoffice/3/user/uno_packages/cache'
removed directory: `.libreoffice/3/user/uno_packages'
removed directory: `.libreoffice/3/user/backup'
removed directory: `.libreoffice/3/user/psprint/fontmetric'
removed `.libreoffice/3/user/psprint/pspfontcache'
removed directory: `.libreoffice/3/user/psprint/driver'
removed directory: `.libreoffice/3/user/psprint'
removed `.libreoffice/3/user/database/biblio/biblio.dbf'
removed `.libreoffice/3/user/database/biblio/biblio.dbt'
removed directory: `.libreoffice/3/user/database/biblio'
removed `.libreoffice/3/user/database/biblio.odb'
removed `.libreoffice/3/user/database/evolocal.odb'
removed directory: `.libreoffice/3/user/database'
removed `.libreoffice/3/user/store/.templdir.cache'
removed directory: `.libreoffice/3/user/store'
removed `.libreoffice/3/user/wordbook/standard.dic'
removed directory: `.libreoffice/3/user/wordbook'
removed directory: `.libreoffice/3/user/template'
removed directory: `.libreoffice/3/user/Scripts'
removed directory: `.libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend'
removed `.libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registered_packages.db'
removed `.libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/backenddb.xml'
removed directory: `.libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend'
removed `.libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/backenddb.xml'
removed directory: `.libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/extensions/shared/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/extensions/shared/registry'
removed `.libreoffice/3/user/extensions/shared/lastsynchronized'
removed `.libreoffice/3/user/extensions/shared/extensions.db'
removed directory: `.libreoffice/3/user/extensions/shared'
removed directory: `.libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend'
removed `.libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registered_packages.db'
removed `.libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/backenddb.xml'
removed directory: `.libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend'
removed `.libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/backenddb.xml'
removed directory: `.libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/extensions/bundled/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/extensions/bundled/registry'
removed `.libreoffice/3/user/extensions/bundled/lastsynchronized'
removed `.libreoffice/3/user/extensions/bundled/extensions.db'
removed directory: `.libreoffice/3/user/extensions/bundled'
removed directory: `.libreoffice/3/user/extensions/tmp/registry/com.sun.star.comp.deployment.script.PackageRegistryBackend'
removed `.libreoffice/3/user/extensions/tmp/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/registered_packages.db'
removed `.libreoffice/3/user/extensions/tmp/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend/backenddb.xml'
removed directory: `.libreoffice/3/user/extensions/tmp/registry/com.sun.star.comp.deployment.configuration.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/extensions/tmp/registry/com.sun.star.comp.deployment.bundle.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/extensions/tmp/registry/com.sun.star.comp.deployment.sfwk.PackageRegistryBackend'
removed `.libreoffice/3/user/extensions/tmp/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend/backenddb.xml'
removed directory: `.libreoffice/3/user/extensions/tmp/registry/com.sun.star.comp.deployment.help.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/extensions/tmp/registry/com.sun.star.comp.deployment.executable.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/extensions/tmp/registry/com.sun.star.comp.deployment.component.PackageRegistryBackend'
removed directory: `.libreoffice/3/user/extensions/tmp/registry'
removed directory: `.libreoffice/3/user/extensions/tmp/extensions'
removed `.libreoffice/3/user/extensions/tmp/extensions.db'
removed directory: `.libreoffice/3/user/extensions/tmp'
removed directory: `.libreoffice/3/user/extensions'
removed `.libreoffice/3/user/config/standard.sod'
removed `.libreoffice/3/user/config/arrowhd_en-US.soe'
removed `.libreoffice/3/user/config/palette_en-US.soc'
removed `.libreoffice/3/user/config/scribus.soc'
removed `.libreoffice/3/user/config/libreoffice.soc'
removed `.libreoffice/3/user/config/tango.soc'
removed `.libreoffice/3/user/config/standard.sog'
removed `.libreoffice/3/user/config/standard.soh'
removed `.libreoffice/3/user/config/cmyk.soc'
removed `.libreoffice/3/user/config/styles_en-US.sod'
removed `.libreoffice/3/user/config/classic_en-US.sog'
removed `.libreoffice/3/user/config/html.soc'
removed `.libreoffice/3/user/config/hatching_en-US.soh'
removed `.libreoffice/3/user/config/javasettings_Linux_X86_64.xml'
removed `.libreoffice/3/user/config/standard.soe'
removed `.libreoffice/3/user/config/web.soc'
removed `.libreoffice/3/user/config/standard.sob'
removed `.libreoffice/3/user/config/autotbl.fmt'
removed `.libreoffice/3/user/config/modern_en-US.sog'
removed `.libreoffice/3/user/config/standard.soc'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/scalc/images/Bitmaps'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/scalc/images'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/scalc/menubar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/scalc/toolbar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/scalc/statusbar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/scalc'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/StartModule/images/Bitmaps'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/StartModule/images'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/StartModule/menubar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/StartModule/toolbar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/StartModule/statusbar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/StartModule'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/dbbrowser/images/Bitmaps'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/dbbrowser/images'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/dbbrowser/menubar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/dbbrowser/toolbar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/dbbrowser/statusbar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/dbbrowser'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/simpress/images/Bitmaps'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/simpress/images'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/simpress/menubar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/simpress/toolbar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/simpress/statusbar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/simpress'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/schart/images/Bitmaps'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/schart/images'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/schart/menubar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/schart/toolbar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/schart/statusbar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/schart'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/swriter/images/Bitmaps'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/swriter/images'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/swriter/menubar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/swriter/toolbar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/swriter/statusbar'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules/swriter'
removed directory: `.libreoffice/3/user/config/soffice.cfg/modules'
removed directory: `.libreoffice/3/user/config/soffice.cfg'
removed `.libreoffice/3/user/config/gallery.soc'
removed directory: `.libreoffice/3/user/config'
removed `.libreoffice/3/user/autotext/mytexts.bau'
removed directory: `.libreoffice/3/user/autotext'
removed directory: `.libreoffice/3/user/temp'
removed `.libreoffice/3/user/registrymodifications.xcu'
removed `.libreoffice/3/user/gallery/youdontownme.wav'
removed `.libreoffice/3/user/gallery/sg30.sdv'
removed `.libreoffice/3/user/gallery/sg30.sdg'
removed `.libreoffice/3/user/gallery/1 - A_I\'m alive.wav'
removed `.libreoffice/3/user/gallery/sg30.thm'
removed `.libreoffice/3/user/gallery/AmazingGrace_Mantovani.wav'
removed `.libreoffice/3/user/gallery/am101.wav'
removed `.libreoffice/3/user/gallery/Forest Gump Theme210.wav'
removed `.libreoffice/3/user/gallery/sg100.thm'
removed `.libreoffice/3/user/gallery/sg100.sdv'
removed directory: `.libreoffice/3/user/gallery'
removed directory: `.libreoffice/3/user/autocorr'
removed directory: `.libreoffice/3/user'
removed directory: `.libreoffice/3'
removed directory: `.libreoffice'
```

sudo apt-get purge libreoffice* | tee purge.txt

```
Reading package lists...
Building dependency tree...
Reading state information...
Package libreoffice-nlpsolver is not installed, so not removed
Package libreoffice-voikko is not installed, so not removed
Package docvert-libreoffice is not installed, so not removed
Package libreoffice-writer2latex is not installed, so not removed
Package libreoffice-writer2xhtml is not installed, so not removed
Package libreoffice-dbg is not installed, so not removed
Package libreoffice-dev is not installed, so not removed
Package libreoffice-dev-doc is not installed, so not removed
Package libreoffice-filter-binfilter is not installed, so not removed
Package libreoffice-gcj is not installed, so not removed
Package libreoffice-gnome is not installed, so not removed
Package libreoffice-gtk is not installed, so not removed
Package libreoffice-help-ca is not installed, so not removed
Package libreoffice-help-cs is not installed, so not removed
Package libreoffice-help-da is not installed, so not removed
Package libreoffice-help-de is not installed, so not removed
Package libreoffice-help-dz is not installed, so not removed
Package libreoffice-help-el is not installed, so not removed
Package libreoffice-help-en-gb is not installed, so not removed
Package libreoffice-help-en-us is not installed, so not removed
Package libreoffice-help-es is not installed, so not removed
Package libreoffice-help-et is not installed, so not removed
Package libreoffice-help-eu is not installed, so not removed
Package libreoffice-help-fi is not installed, so not removed
Package libreoffice-help-fr is not installed, so not removed
Package libreoffice-help-gl is not installed, so not removed
Package libreoffice-help-hi is not installed, so not removed
Package libreoffice-help-hu is not installed, so not removed
Package libreoffice-help-it is not installed, so not removed
Package libreoffice-help-ja is not installed, so not removed
Package libreoffice-help-km is not installed, so not removed
Package libreoffice-help-ko is not installed, so not removed
Package libreoffice-help-nl is not installed, so not removed
Package libreoffice-help-om is not installed, so not removed
Package libreoffice-help-pl is not installed, so not removed
Package libreoffice-help-pt is not installed, so not removed
Package libreoffice-help-pt-br is not installed, so not removed
Package libreoffice-help-ru is not installed, so not removed
Package libreoffice-help-sk is not installed, so not removed
Package libreoffice-help-sl is not installed, so not removed
Package libreoffice-help-sv is not installed, so not removed
Package libreoffice-help-zh-cn is not installed, so not removed
Package libreoffice-help-zh-tw is not installed, so not removed
Package libreoffice-kde is not installed, so not removed
Package libreoffice-l10n-af is not installed, so not removed
Package libreoffice-l10n-ar is not installed, so not removed
Package libreoffice-l10n-as is not installed, so not removed
Package libreoffice-l10n-ast is not installed, so not removed
Package libreoffice-l10n-be-by is not installed, so not removed
Package libreoffice-l10n-bg is not installed, so not removed
Package libreoffice-l10n-bn is not installed, so not removed
Package libreoffice-l10n-br is not installed, so not removed
Package libreoffice-l10n-bs is not installed, so not removed
Package libreoffice-l10n-ca is not installed, so not removed
Package libreoffice-l10n-common is not installed, so not removed
Package libreoffice-l10n-cs is not installed, so not removed
Package libreoffice-l10n-cy is not installed, so not removed
Package libreoffice-l10n-da is not installed, so not removed
Package libreoffice-l10n-de is not installed, so not removed
Package libreoffice-l10n-dz is not installed, so not removed
Package libreoffice-l10n-el is not installed, so not removed
Package libreoffice-l10n-en-gb is not installed, so not removed
Package libreoffice-l10n-en-za is not installed, so not removed
Package libreoffice-l10n-eo is not installed, so not removed
Package libreoffice-l10n-es is not installed, so not removed
Package libreoffice-l10n-et is not installed, so not removed
Package libreoffice-l10n-eu is not installed, so not removed
Package libreoffice-l10n-fa is not installed, so not removed
Package libreoffice-l10n-fi is not installed, so not removed
Package libreoffice-l10n-fr is not installed, so not removed
Package libreoffice-l10n-ga is not installed, so not removed
Package libreoffice-l10n-gl is not installed, so not removed
Package libreoffice-l10n-gu is not installed, so not removed
Package libreoffice-l10n-he is not installed, so not removed
Package libreoffice-l10n-hi is not installed, so not removed
Package libreoffice-l10n-hr is not installed, so not removed
Package libreoffice-l10n-hu is not installed, so not removed
Package libreoffice-l10n-id is not installed, so not removed
Package libreoffice-l10n-in is not installed, so not removed
Package libreoffice-l10n-is is not installed, so not removed
Package libreoffice-l10n-it is not installed, so not removed
Package libreoffice-l10n-ja is not installed, so not removed
Package libreoffice-l10n-ka is not installed, so not removed
Package libreoffice-l10n-km is not installed, so not removed
Package libreoffice-l10n-ko is not installed, so not removed
Package libreoffice-l10n-ku is not installed, so not removed
Package libreoffice-l10n-lt is not installed, so not removed
Package libreoffice-l10n-lv is not installed, so not removed
Package libreoffice-l10n-mk is not installed, so not removed
Package libreoffice-l10n-ml is not installed, so not removed
Package libreoffice-l10n-mn is not installed, so not removed
Package libreoffice-l10n-mr is not installed, so not removed
Package libreoffice-l10n-nb is not installed, so not removed
Package libreoffice-l10n-ne is not installed, so not removed
Package libreoffice-l10n-nl is not installed, so not removed
Package libreoffice-l10n-nn is not installed, so not removed
Package libreoffice-l10n-nr is not installed, so not removed
Package libreoffice-l10n-ns is not installed, so not removed
Package libreoffice-l10n-oc is not installed, so not removed
Package libreoffice-l10n-om is not installed, so not removed
Package libreoffice-l10n-or is not installed, so not removed
Package libreoffice-l10n-pa-in is not installed, so not removed
Package libreoffice-l10n-pl is not installed, so not removed
Package libreoffice-l10n-pt is not installed, so not removed
Package libreoffice-l10n-pt-br is not installed, so not removed
Package libreoffice-l10n-ro is not installed, so not removed
Package libreoffice-l10n-ru is not installed, so not removed
Package libreoffice-l10n-rw is not installed, so not removed
Package libreoffice-l10n-si is not installed, so not removed
Package libreoffice-l10n-sk is not installed, so not removed
Package libreoffice-l10n-sl is not installed, so not removed
Package libreoffice-l10n-sr is not installed, so not removed
Package libreoffice-l10n-ss is not installed, so not removed
Package libreoffice-l10n-st is not installed, so not removed
Package libreoffice-l10n-sv is not installed, so not removed
Package libreoffice-l10n-ta is not installed, so not removed
Package libreoffice-l10n-te is not installed, so not removed
Package libreoffice-l10n-tg is not installed, so not removed
Package libreoffice-l10n-th is not installed, so not removed
Package libreoffice-l10n-tn is not installed, so not removed
Package libreoffice-l10n-tr is not installed, so not removed
Package libreoffice-l10n-ts is not installed, so not removed
Package libreoffice-l10n-ug is not installed, so not removed
Package libreoffice-l10n-uk is not installed, so not removed
Package libreoffice-l10n-uz is not installed, so not removed
Package libreoffice-l10n-ve is not installed, so not removed
Package libreoffice-l10n-vi is not installed, so not removed
Package libreoffice-l10n-xh is not installed, so not removed
Package libreoffice-l10n-za is not installed, so not removed
Package libreoffice-l10n-zh-cn is not installed, so not removed
Package libreoffice-l10n-zh-tw is not installed, so not removed
Package libreoffice-l10n-zu is not installed, so not removed
Package libreoffice-officebean is not installed, so not removed
Package libreoffice-style-andromeda is not installed, so not removed
Package libreoffice-style-oxygen is not installed, so not removed
Package libreoffice-style-tango is not installed, so not removed
Package libreoffice-evolution is not installed, so not removed
Package libreoffice-mysql-connector is not installed, so not removed
Package libreoffice-ogltrans is not installed, so not removed
Package libreoffice-pdfimport is not installed, so not removed
Package libreoffice-presentation-minimizer is not installed, so not removed
Package libreoffice-presenter-console is not installed, so not removed
Package libreoffice-report-builder is not installed, so not removed
Package libreoffice-sdbc-postgresql is not installed, so not removed
Package libreoffice-style-crystal is not installed, so not removed
Package libreoffice-style-galaxy is not installed, so not removed
Package libreoffice-style-hicontrast is not installed, so not removed
Package libreoffice-wiki-publisher is not installed, so not removed
Package mozilla-libreoffice is not installed, so not removed
Package openclipart-libreoffice is not installed, so not removed
Package openoffice.org-dtd-officedocument1.0 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  librdf0 libtextcat-data libhyphen0 ttf-sil-gentium libhsqldb-java librasqal2
  ttf-sil-gentium-basic libtextcat0 xfonts-mathml libraptor1 libgraphite3
  libmythes-1.2-0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libreoffice* libreoffice-base* libreoffice-base-core* libreoffice-calc*
  libreoffice-common* libreoffice-core* libreoffice-draw*
  libreoffice-emailmerge* libreoffice-filter-mobiledev* libreoffice-impress*
  libreoffice-java-common* libreoffice-math* libreoffice-report-builder-bin*
  libreoffice-style-human* libreoffice-writer* python-uno*
0 upgraded, 0 newly installed, 16 to remove and 0 not upgraded.
After this operation, 261 MB disk space will be freed.
Do you want to continue [Y/n]? (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 262551 files and directories currently installed.)

Removing libreoffice ...

Removing libreoffice-report-builder-bin ...

Removing libreoffice-base ...

Purging configuration files for libreoffice-base ...

Removing libreoffice-writer ...

Purging configuration files for libreoffice-writer ...

Removing libreoffice-calc ...

Purging configuration files for libreoffice-calc ...

Removing libreoffice-base-core ...

Removing libreoffice-filter-mobiledev ...

Removing libreoffice-java-common ...

Removing libreoffice-emailmerge ...

Removing python-uno ...

Removing libreoffice-math ...

Purging configuration files for libreoffice-math ...

Removing libreoffice-impress ...

Purging configuration files for libreoffice-impress ...

Removing libreoffice-draw ...

Purging configuration files for libreoffice-draw ...

Removing libreoffice-common ...

Purging configuration files for libreoffice-common ...

Removing libreoffice-style-human ...

Removing libreoffice-core ...

Purging configuration files for libreoffice-core ...

Processing triggers for man-db ...

Processing triggers for desktop-file-utils ...

Processing triggers for python-gmenu ...

Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...

Processing triggers for shared-mime-info ...

Processing triggers for hicolor-icon-theme ...

Processing triggers for python-support ...
```

and just to check
```
19:43:19 ~ ls /var/lib/
acpi-support         gconf            nfs             synaptic
alsa                 gdm              ntpdate         ucf
apt                  ghostscript      os-prober       udisks
aptitude             hp               pam             update-manager
apt-xapian-index     initramfs-tools  partconf        update-notifier
aspell               initscripts      partman         update-rc.d
avahi-autoipd        insserv          plymouth        upower
belocs               jetty            polkit-1        urandom
dbus                 libuuid          pulseaudio      ureadahead
defoma               lintian          pycentral       usb_modeswitch
dhcp                 localechooser    python-support  usbutils
dictionaries-common  locales          samba           vim
dkms                 logrotate        security        wicd
doc-base             misc             sgml-base       xfonts
dpkg                 mlocate          snmp            xkb
emacsen-common       NetworkManager   sudo            xml-core
19:46:10 ~ ls /var/spool
anacron  cron  cups  lintian  mail  plymouth

```

no libreoffice directories
you might consider
```
sudo rm -r /var/lib/libreoffice
sudo rm -r /var/spool/libreoffice
```

be very careful not to put any spaces in that path

sudo apt-get install libreoffice | tee install.txt
```
Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  libreoffice-base libreoffice-base-core libreoffice-calc libreoffice-common
  libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-filter-mobiledev libreoffice-impress libreoffice-java-common
  libreoffice-math libreoffice-report-builder-bin libreoffice-style-human
  libreoffice-writer python-uno
Suggested packages:
  libreoffice-help-3.3.3 menu unixodbc hyphen-hyphenation-patterns
  mythes-thesaurus libreoffice-gnome libreoffice-kde openclipart-libreoffice
  pstoedit imagemagick graphicsmagick-imagemagick-compat
  libreoffice-filter-binfilter libreoffice-officebean libmyodbc
  odbc-postgresql libsqliteodbc tdsodbc mdbtools libmysql-java libpg-java
  libjtds-java libreoffice-gcj libreoffice-report-builder
  libreoffice-style-hicontrast libreoffice-style-tango
  libreoffice-style-crystal libreoffice-style-oxygen bsh kde-icons-crystal
  crystalcursors
The following NEW packages will be installed:
  libreoffice libreoffice-base libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-filter-mobiledev libreoffice-impress libreoffice-java-common
  libreoffice-math libreoffice-report-builder-bin libreoffice-style-human
  libreoffice-writer python-uno
0 upgraded, 16 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/69.5 MB of archives.
After this operation, 261 MB of additional disk space will be used.
Do you want to continue [Y/n]? Selecting previously deselected package libreoffice-style-human.

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 259805 files and directories currently installed.)

Unpacking libreoffice-style-human (from .../libreoffice-style-human_1%3a3.3.3-1ubuntu2_all.deb) ...

Selecting previously deselected package libreoffice-common.

Unpacking libreoffice-common (from .../libreoffice-common_1%3a3.3.3-1ubuntu2_all.deb) ...

Selecting previously deselected package libreoffice-core.

Unpacking libreoffice-core (from .../libreoffice-core_1%3a3.3.3-1ubuntu2_amd64.deb) ...

Selecting previously deselected package libreoffice-base-core.

Unpacking libreoffice-base-core (from .../libreoffice-base-core_1%3a3.3.3-1ubuntu2_amd64.deb) ...

Selecting previously deselected package libreoffice-writer.

Unpacking libreoffice-writer (from .../libreoffice-writer_1%3a3.3.3-1ubuntu2_amd64.deb) ...

Selecting previously deselected package libreoffice-calc.

Unpacking libreoffice-calc (from .../libreoffice-calc_1%3a3.3.3-1ubuntu2_amd64.deb) ...

Selecting previously deselected package libreoffice-draw.

Unpacking libreoffice-draw (from .../libreoffice-draw_1%3a3.3.3-1ubuntu2_amd64.deb) ...

Selecting previously deselected package libreoffice-impress.

Unpacking libreoffice-impress (from .../libreoffice-impress_1%3a3.3.3-1ubuntu2_amd64.deb) ...

Selecting previously deselected package libreoffice-math.

Unpacking libreoffice-math (from .../libreoffice-math_1%3a3.3.3-1ubuntu2_amd64.deb) ...

Selecting previously deselected package libreoffice-java-common.

Unpacking libreoffice-java-common (from .../libreoffice-java-common_1%3a3.3.3-1ubuntu2_all.deb) ...

Selecting previously deselected package libreoffice-base.

Unpacking libreoffice-base (from .../libreoffice-base_1%3a3.3.3-1ubuntu2_amd64.deb) ...

Selecting previously deselected package libreoffice-report-builder-bin.

Unpacking libreoffice-report-builder-bin (from .../libreoffice-report-builder-bin_1%3a3.3.3-1ubuntu2_amd64.deb) ...

Selecting previously deselected package libreoffice-filter-mobiledev.

Unpacking libreoffice-filter-mobiledev (from .../libreoffice-filter-mobiledev_1%3a3.3.3-1ubuntu2_all.deb) ...

Selecting previously deselected package libreoffice.

Unpacking libreoffice (from .../libreoffice_1%3a3.3.3-1ubuntu2_amd64.deb) ...

Selecting previously deselected package python-uno.

Unpacking python-uno (from .../python-uno_1%3a3.3.3-1ubuntu2_amd64.deb) ...

Selecting previously deselected package libreoffice-emailmerge.

Unpacking libreoffice-emailmerge (from .../libreoffice-emailmerge_1%3a3.3.3-1ubuntu2_all.deb) ...

Processing triggers for man-db ...

Processing triggers for hicolor-icon-theme ...

Processing triggers for desktop-file-utils ...

Processing triggers for python-gmenu ...

Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...

Processing triggers for shared-mime-info ...

Processing triggers for python-support ...

Setting up libreoffice-core (1:3.3.3-1ubuntu2) ...

Setting up libreoffice-style-human (1:3.3.3-1ubuntu2) ...

Setting up libreoffice-base-core (1:3.3.3-1ubuntu2) ...

Setting up libreoffice-writer (1:3.3.3-1ubuntu2) ...

Setting up libreoffice-calc (1:3.3.3-1ubuntu2) ...

Setting up libreoffice-draw (1:3.3.3-1ubuntu2) ...

Setting up libreoffice-impress (1:3.3.3-1ubuntu2) ...

Setting up libreoffice-math (1:3.3.3-1ubuntu2) ...

Setting up python-uno (1:3.3.3-1ubuntu2) ...

Setting up libreoffice-emailmerge (1:3.3.3-1ubuntu2) ...

Setting up libreoffice-common (1:3.3.3-1ubuntu2) ...

Setting up libreoffice-java-common (1:3.3.3-1ubuntu2) ...

Setting up libreoffice-base (1:3.3.3-1ubuntu2) ...

Setting up libreoffice-report-builder-bin (1:3.3.3-1ubuntu2) ...

Setting up libreoffice-filter-mobiledev (1:3.3.3-1ubuntu2) ...

Setting up libreoffice (1:3.3.3-1ubuntu2) ...
```

I noticed when I opened it the first time I have that "loading documents" box for a few seconds before it opened.
If that is where your system is hanging it could be a corupt
file that's not being deleted.

jdb

---

### Post by flo1805 on 2011-08-21
ok...I did the same you did:


```
florian@system:~$ sudo rm -rfv .libreoffice*
removed `.libreoffice/3/user/psprint/pspfontcache'
removed directory: `.libreoffice/3/user/psprint'
removed `.libreoffice/3/user/config/javasettings_Linux_X86_64.xml'
removed directory: `.libreoffice/3/user/config'
removed directory: `.libreoffice/3/user/extensions/bundled'
removed directory: `.libreoffice/3/user/extensions'
removed directory: `.libreoffice/3/user'
removed directory: `.libreoffice/3'
removed directory: `.libreoffice'
florian@system:~$ sudo apt-get purge libreoffice*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libreoffice-writer' for regex 'libreoffice*'
Note, selecting 'libreoffice-calc' for regex 'libreoffice*'
Note, selecting 'libreoffice-impress' for regex 'libreoffice*'
Note, selecting 'libreoffice-kde' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-oxygen' for regex 'libreoffice*'
Note, selecting 'libreoffice-base' for regex 'libreoffice*'
Note, selecting 'libreoffice-core' for regex 'libreoffice*'
Note, selecting 'libreoffice-base-core' for regex 'libreoffice*'
Note, selecting 'libreoffice-java-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-gcj' for regex 'libreoffice*'
Note, selecting 'libreoffice-report-builder' for regex 'libreoffice*'
Note, selecting 'libreoffice-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-default' for regex 'libreoffice*'
Note, selecting 'libreoffice-style' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-hicontrast' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-tango' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-crystal' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-human' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-andromeda' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-galaxy' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-industrial' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-us' for regex 'libreoffice*'
Note, selecting 'libreoffice-dev' for regex 'libreoffice*'
Note, selecting 'libreoffice-draw' for regex 'libreoffice*'
Note, selecting 'libreoffice-evolution' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-so52' for regex 'libreoffice*'
Note, selecting 'libreoffice-gnome' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk' for regex 'libreoffice*'
Note, selecting 'libreoffice-officebean' for regex 'libreoffice*'
Note, selecting 'libreoffice-bundled' for regex 'libreoffice*'
Note, selecting 'libreoffice-dbg' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-binfilter' for regex 'libreoffice*'
Note, selecting 'mozilla-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-ogltrans' for regex 'libreoffice*'
Note, selecting 'libreoffice-dev-doc' for regex 'libreoffice*'
Note, selecting 'libreoffice-dtd-officedocument1.0' for regex 'libreoffice*'
Note, selecting 'libreoffice-emailmerge' for regex 'libreoffice*'
Note, selecting 'libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk-gnome' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-3.3.2' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-gb' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-gb' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-us' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pt-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pt-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sv' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sv' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zh-tw' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zh-tw' for regex 'libreoffice*'
Note, selecting 'libreoffice-kab' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-3.3.2' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ast' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ast' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-be-by' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-be-by' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-ctl-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-or' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ta' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-te' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ku' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ku' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ns' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ns' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-or' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-rw' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-rw' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-si' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-si' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ss' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ss' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-st' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-st' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ta' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-te' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tg' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tg' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-th' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-th' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ts' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ts' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ug' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ug' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-uk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-uk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-uz' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-uz' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ve' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ve' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-vi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-vi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-xh' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-xh' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zu' for regex 'libreoffice*'
Note, selecting 'libreoffice-math' for regex 'libreoffice*'
Note, selecting 'libreoffice-nlpsolver' for regex 'libreoffice*'
Note, selecting 'libreoffice-voikko' for regex 'libreoffice*'
Note, selecting 'libreoffice-hyphenation-fi' for regex 'libreoffice*'
Note, selecting 'docvert-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-report-builder-bin' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-mobiledev' for regex 'libreoffice*'
Note, selecting 'openclipart-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-mysql-connector' for regex 'libreoffice*'
Note, selecting 'libreoffice-pdfimport' for regex 'libreoffice*'
Note, selecting 'libreoffice-presentation-minimizer' for regex 'libreoffice*'
Note, selecting 'libreoffice-presenter-console' for regex 'libreoffice*'
Note, selecting 'libreoffice-reportdesigner' for regex 'libreoffice*'
Note, selecting 'libreoffice-sdbc-postgresql' for regex 'libreoffice*'
Note, selecting 'libreoffice-wiki-publisher' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer2latex' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer2xhtml' for regex 'libreoffice*'
Note, selecting 'libreoffice-dmaths' for regex 'libreoffice*'
Note, selecting 'libreoffice-zemberek' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-3.3.3' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-3.3.3' for regex 'libreoffice*'
Note, selecting 'libreoffice3.3-mandriva-menus' for regex 'libreoffice*'
Note, selecting 'libreoffice3.3-redhat-menus' for regex 'libreoffice*'
Note, selecting 'libreoffice3.3-suse-menus' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-human' instead of 'libreoffice-style-default'
Note, selecting 'libreoffice-common' instead of 'libreoffice-l10n-en-us'
Note, selecting 'libreoffice-core' instead of 'libreoffice-bundled'
Note, selecting 'openoffice.org-dtd-officedocument1.0' instead of 'libreoffice-dtd-officedocument1.0'
Note, selecting 'libreoffice-gnome' instead of 'libreoffice-gtk-gnome'
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-spellcheck-fi'
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-hyphenation-fi'
Note, selecting 'libreoffice-report-builder' instead of 'libreoffice-reportdesigner'
Package libreoffice-nlpsolver is not installed, so not removed
Package libreoffice-voikko is not installed, so not removed
Package docvert-libreoffice is not installed, so not removed
Package libreoffice-writer2latex is not installed, so not removed
Package libreoffice-writer2xhtml is not installed, so not removed
Package libreoffice-dbg is not installed, so not removed
Package libreoffice-dev is not installed, so not removed
Package libreoffice-dev-doc is not installed, so not removed
Package libreoffice-filter-binfilter is not installed, so not removed
Package libreoffice-gcj is not installed, so not removed
Package libreoffice-gnome is not installed, so not removed
Package libreoffice-gtk is not installed, so not removed
Package libreoffice-help-ca is not installed, so not removed
Package libreoffice-help-cs is not installed, so not removed
Package libreoffice-help-da is not installed, so not removed
Package libreoffice-help-de is not installed, so not removed
Package libreoffice-help-dz is not installed, so not removed
Package libreoffice-help-el is not installed, so not removed
Package libreoffice-help-en-gb is not installed, so not removed
Package libreoffice-help-en-us is not installed, so not removed
Package libreoffice-help-es is not installed, so not removed
Package libreoffice-help-et is not installed, so not removed
Package libreoffice-help-eu is not installed, so not removed
Package libreoffice-help-fi is not installed, so not removed
Package libreoffice-help-fr is not installed, so not removed
Package libreoffice-help-gl is not installed, so not removed
Package libreoffice-help-hi is not installed, so not removed
Package libreoffice-help-hu is not installed, so not removed
Package libreoffice-help-it is not installed, so not removed
Package libreoffice-help-ja is not installed, so not removed
Package libreoffice-help-km is not installed, so not removed
Package libreoffice-help-ko is not installed, so not removed
Package libreoffice-help-nl is not installed, so not removed
Package libreoffice-help-om is not installed, so not removed
Package libreoffice-help-pl is not installed, so not removed
Package libreoffice-help-pt is not installed, so not removed
Package libreoffice-help-pt-br is not installed, so not removed
Package libreoffice-help-ru is not installed, so not removed
Package libreoffice-help-sk is not installed, so not removed
Package libreoffice-help-sl is not installed, so not removed
Package libreoffice-help-sv is not installed, so not removed
Package libreoffice-help-zh-cn is not installed, so not removed
Package libreoffice-help-zh-tw is not installed, so not removed
Package libreoffice-kde is not installed, so not removed
Package libreoffice-l10n-af is not installed, so not removed
Package libreoffice-l10n-ar is not installed, so not removed
Package libreoffice-l10n-as is not installed, so not removed
Package libreoffice-l10n-ast is not installed, so not removed
Package libreoffice-l10n-be-by is not installed, so not removed
Package libreoffice-l10n-bg is not installed, so not removed
Package libreoffice-l10n-bn is not installed, so not removed
Package libreoffice-l10n-br is not installed, so not removed
Package libreoffice-l10n-bs is not installed, so not removed
Package libreoffice-l10n-ca is not installed, so not removed
Package libreoffice-l10n-common is not installed, so not removed
Package libreoffice-l10n-cs is not installed, so not removed
Package libreoffice-l10n-cy is not installed, so not removed
Package libreoffice-l10n-da is not installed, so not removed
Package libreoffice-l10n-de is not installed, so not removed
Package libreoffice-l10n-dz is not installed, so not removed
Package libreoffice-l10n-el is not installed, so not removed
Package libreoffice-l10n-en-gb is not installed, so not removed
Package libreoffice-l10n-en-za is not installed, so not removed
Package libreoffice-l10n-eo is not installed, so not removed
Package libreoffice-l10n-es is not installed, so not removed
Package libreoffice-l10n-et is not installed, so not removed
Package libreoffice-l10n-eu is not installed, so not removed
Package libreoffice-l10n-fa is not installed, so not removed
Package libreoffice-l10n-fi is not installed, so not removed
Package libreoffice-l10n-fr is not installed, so not removed
Package libreoffice-l10n-ga is not installed, so not removed
Package libreoffice-l10n-gl is not installed, so not removed
Package libreoffice-l10n-gu is not installed, so not removed
Package libreoffice-l10n-he is not installed, so not removed
Package libreoffice-l10n-hi is not installed, so not removed
Package libreoffice-l10n-hr is not installed, so not removed
Package libreoffice-l10n-hu is not installed, so not removed
Package libreoffice-l10n-id is not installed, so not removed
Package libreoffice-l10n-in is not installed, so not removed
Package libreoffice-l10n-is is not installed, so not removed
Package libreoffice-l10n-it is not installed, so not removed
Package libreoffice-l10n-ja is not installed, so not removed
Package libreoffice-l10n-ka is not installed, so not removed
Package libreoffice-l10n-km is not installed, so not removed
Package libreoffice-l10n-ko is not installed, so not removed
Package libreoffice-l10n-ku is not installed, so not removed
Package libreoffice-l10n-lt is not installed, so not removed
Package libreoffice-l10n-lv is not installed, so not removed
Package libreoffice-l10n-mk is not installed, so not removed
Package libreoffice-l10n-ml is not installed, so not removed
Package libreoffice-l10n-mn is not installed, so not removed
Package libreoffice-l10n-mr is not installed, so not removed
Package libreoffice-l10n-nb is not installed, so not removed
Package libreoffice-l10n-ne is not installed, so not removed
Package libreoffice-l10n-nl is not installed, so not removed
Package libreoffice-l10n-nn is not installed, so not removed
Package libreoffice-l10n-nr is not installed, so not removed
Package libreoffice-l10n-ns is not installed, so not removed
Package libreoffice-l10n-oc is not installed, so not removed
Package libreoffice-l10n-om is not installed, so not removed
Package libreoffice-l10n-or is not installed, so not removed
Package libreoffice-l10n-pa-in is not installed, so not removed
Package libreoffice-l10n-pl is not installed, so not removed
Package libreoffice-l10n-pt is not installed, so not removed
Package libreoffice-l10n-pt-br is not installed, so not removed
Package libreoffice-l10n-ro is not installed, so not removed
Package libreoffice-l10n-ru is not installed, so not removed
Package libreoffice-l10n-rw is not installed, so not removed
Package libreoffice-l10n-si is not installed, so not removed
Package libreoffice-l10n-sk is not installed, so not removed
Package libreoffice-l10n-sl is not installed, so not removed
Package libreoffice-l10n-sr is not installed, so not removed
Package libreoffice-l10n-ss is not installed, so not removed
Package libreoffice-l10n-st is not installed, so not removed
Package libreoffice-l10n-sv is not installed, so not removed
Package libreoffice-l10n-ta is not installed, so not removed
Package libreoffice-l10n-te is not installed, so not removed
Package libreoffice-l10n-tg is not installed, so not removed
Package libreoffice-l10n-th is not installed, so not removed
Package libreoffice-l10n-tn is not installed, so not removed
Package libreoffice-l10n-tr is not installed, so not removed
Package libreoffice-l10n-ts is not installed, so not removed
Package libreoffice-l10n-ug is not installed, so not removed
Package libreoffice-l10n-uk is not installed, so not removed
Package libreoffice-l10n-uz is not installed, so not removed
Package libreoffice-l10n-ve is not installed, so not removed
Package libreoffice-l10n-vi is not installed, so not removed
Package libreoffice-l10n-xh is not installed, so not removed
Package libreoffice-l10n-za is not installed, so not removed
Package libreoffice-l10n-zh-cn is not installed, so not removed
Package libreoffice-l10n-zh-tw is not installed, so not removed
Package libreoffice-l10n-zu is not installed, so not removed
Package libreoffice-officebean is not installed, so not removed
Package libreoffice-style-andromeda is not installed, so not removed
Package libreoffice-style-oxygen is not installed, so not removed
Package libreoffice-style-tango is not installed, so not removed
Package libreoffice-evolution is not installed, so not removed
Package libreoffice-mysql-connector is not installed, so not removed
Package libreoffice-ogltrans is not installed, so not removed
Package libreoffice-pdfimport is not installed, so not removed
Package libreoffice-presentation-minimizer is not installed, so not removed
Package libreoffice-presenter-console is not installed, so not removed
Package libreoffice-report-builder is not installed, so not removed
Package libreoffice-sdbc-postgresql is not installed, so not removed
Package libreoffice-style-crystal is not installed, so not removed
Package libreoffice-style-galaxy is not installed, so not removed
Package libreoffice-style-hicontrast is not installed, so not removed
Package libreoffice-wiki-publisher is not installed, so not removed
Package mozilla-libreoffice is not installed, so not removed
Package openclipart-libreoffice is not installed, so not removed
Package openoffice.org-dtd-officedocument1.0 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  kubuntu-debug-installer libdbusmenu-qt2 qapt-batch pwgen virtuoso-minimal
  libqca2 docvert libqt4-declarative libbase-java-openoffice.org
  ttf-dejavu-extra libpolkit-qt-1-1 libgcj-bc pdf2svg libknewstuff3-4
  libqapt-runtime php5-xsl libvirtodbc0 libmysqlcppconn4 libnepomukquery4a
  libqt4-script libqt4-network libqt4-dbus bsh-gcj libsac-java-gcj
  libthreadweaver4 libkdecore5 phonon libnepomukutils4 libktexteditor4
  ttf-indic-fonts voikko-fi libkmediaplayer4 ttf-sil-gentium docbook-xsl
  oxygen-icon-theme plasma-scriptengine-javascript libapr1
  libflute-java-openoffice.org libkrosscore4 libhsqldb-java gcj-jre
  ttf-dzongkha libapache2-mod-php5 libloader-java-openoffice.org
  libcommons-logging-java libaprutil1-ldap php5-tidy apache2-mpm-prefork
  ttf-devanagari-fonts php5-gd virtuoso-opensource-6.1-bin libqt4-opengl
  libmysqlclient16 apache2-utils libgcj11 libsolid4 ttf-khmeros librsvg2-bin
  libqt4-xmlpatterns libhsqldb-java-gcj libnepomuk4 ttf-gujarati-fonts
  appmenu-qt ure-dbg libsoprano4 ttf-arabeyes jpegoptim
  libformula-java-openoffice.org virtuoso-opensource-6.1-common
  ttf-telugu-fonts libkdnssd4 libkparts4 apache2.2-common
  plasma-scriptengine-declarative libclucene0ldbl
  libserializer-java-openoffice.org bsh libqapt1 shared-desktop-ontologies
  fckeditor ttf-bengali-fonts kdoctools libqtcore4 libgif4 libsac-java
  libreadline5 libaprutil1-dbd-sqlite3 culmus gcj-4.5-jre-headless
  apache2.2-bin icoutils libkidletime4 gcj-4.5-base libkcmutils4
  ttf-malayalam-fonts libntrack0 soprano-daemon libqt4-sql libkfile4
  libqt4-svg libservlet2.5-java libkpty4 ttf-sil-gentium-basic
  libcommons-httpclient-java gcj-jre-headless gcj-4.5-jre-lib libphonon4
  libpentaho-reporting-flow-engine-java-openoffice.org ttf-tamil-fonts
  libqt4-xml libkntlm4 ttf-farsiweb libplasma3 ttf-dejavu libphp-pclzip
  phonon-backend-gstreamer libkemoticons4 ntrack-module-libnl-0 kdelibs-bin
  libgcj11-awt libkdewebkit5 libqtgui4 libattica0 dmake libkjsembed4 libkio5
  libpq5 libkjsapi4 libstreams0 libcommons-codec-java libcommons-lang-java
  openclipart-png libntrack-qt4-1 libvoikko1 ttf-kannada-fonts kdelibs5-data
  kdebase-runtime gcj-4.5-jre libgcj-common libqt4-sql-mysql php5-cli
  libqtwebkit4 uno-libs3-dbg libssh-4 libaudio2 libknotifyconfig4
  liblayout-java-openoffice.org kdebase-runtime-data libaprutil1
  ttf-oriya-fonts kdelibs5-plugins libiodbc2 libkhtml5 libkdeui5 mysql-common
  php5-common libjline-java libkdesu5 librepository-java-openoffice.org
  libkatepartinterfaces4 optipng libxml-java-openoffice.org libtidy-0.99-0
  libfonts-java-openoffice.org libstreamanalyzer0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libreoffice* libreoffice-base* libreoffice-base-core* libreoffice-calc*
  libreoffice-common* libreoffice-core* libreoffice-draw*
  libreoffice-emailmerge* libreoffice-filter-mobiledev* libreoffice-impress*
  libreoffice-java-common* libreoffice-math* libreoffice-report-builder-bin*
  libreoffice-style-human* libreoffice-writer* python-uno*
0 upgraded, 0 newly installed, 16 to remove and 14 not upgraded.
After this operation, 261 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 211183 files and directories currently installed.)
Removing libreoffice ...
Removing libreoffice-report-builder-bin ...
Removing libreoffice-base ...
Purging configuration files for libreoffice-base ...
Removing libreoffice-writer ...
Purging configuration files for libreoffice-writer ...
Removing libreoffice-calc ...
Purging configuration files for libreoffice-calc ...
Removing libreoffice-base-core ...
Removing libreoffice-filter-mobiledev ...
Removing libreoffice-java-common ...
Removing libreoffice-emailmerge ...
Removing python-uno ...
Removing libreoffice-math ...
Purging configuration files for libreoffice-math ...
Removing libreoffice-impress ...
Purging configuration files for libreoffice-impress ...
Removing libreoffice-draw ...
Purging configuration files for libreoffice-draw ...
Removing libreoffice-common ...
Purging configuration files for libreoffice-common ...
Removing libreoffice-style-human ...
Removing libreoffice-core ...
Purging configuration files for libreoffice-core ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
florian@system:~$ ls /var/lib/
acpi-support         docvert                NetworkManager  ubiquity
alien                dpkg                   ntpdate         ucf
alsa                 flashplugin-installer  os-prober       udisks
apt                  gcj-4.5                pam             update-manager
apt-xapian-index     gconf                  php5            update-notifier
aspell               gdm                    plymouth        update-rc.d
avahi-autoipd        ghostscript            polkit-1        upower
belocs               hp                     pulseaudio      urandom
binfmts              initramfs-tools        pycentral       ureadahead
bluetooth            initscripts            python-support  usb_modeswitch
computer-janitor     insserv                rpm             usbutils
dbus                 libuuid                samba           vim
defoma               lintian                security        xfonts
dhcp                 locales                sgml-base       xkb
dictionaries-common  logrotate              snmp            xml-core
dkms                 misc                   sudo
doc-base             mlocate                synaptic
florian@system:~$ ls /var/spool/
anacron  cron  cups  lintian  lpd  mail  plymouth
florian@system:~$ sudo apt-get install libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kubuntu-debug-installer libdbusmenu-qt2 qapt-batch pwgen virtuoso-minimal
  libqca2 docvert libqt4-declarative libbase-java-openoffice.org
  libpolkit-qt-1-1 libgcj-bc pdf2svg libknewstuff3-4 libqapt-runtime php5-xsl
  libvirtodbc0 libmysqlcppconn4 libnepomukquery4a libqt4-script libqt4-network
  libqt4-dbus bsh-gcj libsac-java-gcj libthreadweaver4 libkdecore5 phonon
  libnepomukutils4 libktexteditor4 ttf-indic-fonts voikko-fi libkmediaplayer4
  docbook-xsl oxygen-icon-theme plasma-scriptengine-javascript libapr1
  libflute-java-openoffice.org libkrosscore4 ttf-dzongkha libapache2-mod-php5
  libloader-java-openoffice.org libcommons-logging-java libaprutil1-ldap
  php5-tidy apache2-mpm-prefork ttf-devanagari-fonts php5-gd
  virtuoso-opensource-6.1-bin libqt4-opengl libmysqlclient16 apache2-utils
  libsolid4 ttf-khmeros librsvg2-bin libqt4-xmlpatterns libhsqldb-java-gcj
  libnepomuk4 ttf-gujarati-fonts appmenu-qt ure-dbg libsoprano4 ttf-arabeyes
  jpegoptim libformula-java-openoffice.org virtuoso-opensource-6.1-common
  ttf-telugu-fonts libkdnssd4 libkparts4 apache2.2-common
  plasma-scriptengine-declarative libclucene0ldbl
  libserializer-java-openoffice.org bsh libqapt1 shared-desktop-ontologies
  fckeditor ttf-bengali-fonts kdoctools libqtcore4 libgif4 libsac-java
  libreadline5 libaprutil1-dbd-sqlite3 culmus apache2.2-bin icoutils
  libkidletime4 libkcmutils4 ttf-malayalam-fonts libntrack0 soprano-daemon
  libqt4-sql libkfile4 libqt4-svg libkpty4 libcommons-httpclient-java
  libphonon4 libpentaho-reporting-flow-engine-java-openoffice.org
  ttf-tamil-fonts libqt4-xml libkntlm4 ttf-farsiweb libplasma3 libphp-pclzip
  phonon-backend-gstreamer libkemoticons4 ntrack-module-libnl-0 kdelibs-bin
  libkdewebkit5 libqtgui4 libattica0 dmake libkjsembed4 libkio5 libpq5
  libkjsapi4 libstreams0 libcommons-codec-java libcommons-lang-java
  openclipart-png libntrack-qt4-1 libvoikko1 ttf-kannada-fonts kdelibs5-data
  kdebase-runtime libqt4-sql-mysql php5-cli libqtwebkit4 uno-libs3-dbg
  libssh-4 libaudio2 libknotifyconfig4 liblayout-java-openoffice.org
  kdebase-runtime-data libaprutil1 ttf-oriya-fonts kdelibs5-plugins libiodbc2
  libkhtml5 libkdeui5 mysql-common php5-common libjline-java libkdesu5
  librepository-java-openoffice.org libkatepartinterfaces4 optipng
  libxml-java-openoffice.org libtidy-0.99-0 libfonts-java-openoffice.org
  libstreamanalyzer0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-base libreoffice-base-core libreoffice-calc libreoffice-common
  libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-filter-mobiledev libreoffice-impress libreoffice-java-common
  libreoffice-math libreoffice-report-builder-bin libreoffice-style-human
  libreoffice-writer python-uno
Suggested packages:
  hunspell-dictionary myspell-dictionary libreoffice-help-3.3.3 menu
  hyphen-hyphenation-patterns mythes-thesaurus libreoffice-gnome
  libreoffice-kde openclipart-libreoffice pstoedit imagemagick
  graphicsmagick-imagemagick-compat libreoffice-filter-binfilter
  libreoffice-officebean libmyodbc odbc-postgresql libsqliteodbc tdsodbc
  mdbtools libmysql-java libpg-java libjtds-java libreoffice-gcj
  libreoffice-report-builder libreoffice-style-hicontrast
  libreoffice-style-tango libreoffice-style-crystal libreoffice-style-oxygen
  kde-icons-crystal crystalcursors
The following NEW packages will be installed:
  libreoffice libreoffice-base libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-filter-mobiledev libreoffice-impress libreoffice-java-common
  libreoffice-math libreoffice-report-builder-bin libreoffice-style-human
  libreoffice-writer python-uno
0 upgraded, 16 newly installed, 0 to remove and 14 not upgraded.
Need to get 0 B/69.5 MB of archives.
After this operation, 261 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libreoffice-style-human.
(Reading database ... 208435 files and directories currently installed.)
Unpacking libreoffice-style-human (from .../libreoffice-style-human_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-common.
Unpacking libreoffice-common (from .../libreoffice-common_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-core.
Unpacking libreoffice-core (from .../libreoffice-core_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-base-core.
Unpacking libreoffice-base-core (from .../libreoffice-base-core_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-writer.
Unpacking libreoffice-writer (from .../libreoffice-writer_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-calc.
Unpacking libreoffice-calc (from .../libreoffice-calc_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-draw.
Unpacking libreoffice-draw (from .../libreoffice-draw_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-impress.
Unpacking libreoffice-impress (from .../libreoffice-impress_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-math.
Unpacking libreoffice-math (from .../libreoffice-math_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-java-common.
Unpacking libreoffice-java-common (from .../libreoffice-java-common_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice-base.
Unpacking libreoffice-base (from .../libreoffice-base_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-report-builder-bin.
Unpacking libreoffice-report-builder-bin (from .../libreoffice-report-builder-bin_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-filter-mobiledev.
Unpacking libreoffice-filter-mobiledev (from .../libreoffice-filter-mobiledev_1%3a3.3.3-1ubuntu2_all.deb) ...
Selecting previously deselected package libreoffice.
Unpacking libreoffice (from .../libreoffice_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package python-uno.
Unpacking python-uno (from .../python-uno_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libreoffice-emailmerge.
Unpacking libreoffice-emailmerge (from .../libreoffice-emailmerge_1%3a3.3.3-1ubuntu2_all.deb) ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for python-support ...
Setting up libreoffice-core (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-style-human (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-base-core (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-writer (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-calc (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-draw (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-impress (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-math (1:3.3.3-1ubuntu2) ...
Setting up python-uno (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-emailmerge (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-common (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-java-common (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-base (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-report-builder-bin (1:3.3.3-1ubuntu2) ...
Setting up libreoffice-filter-mobiledev (1:3.3.3-1ubuntu2) ...
Setting up libreoffice (1:3.3.3-1ubuntu2) ...
florian@system:~$ 

```and surprise...

```
florian@system:~$ libreoffice
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'
florian@system:~$ 

```

---

### Post by sanderd17 on 2011-08-21
> **flo1805 said:**
> ok...I did the same you did:

snip

and surprise...

```
florian@system:~$ libreoffice
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'
florian@system:~$ 

```

Ok, so it is a bug in the libreoffice package, I filed a bug report: [https://bugs.edge.launchpad.net/ubuntu/+source/libreoffice/+bug/830481](https://bugs.edge.launchpad.net/ubuntu/+source/libreoffice/+bug/830481)

---

### Post by flo1805 on 2011-08-21
ok. thanks. and what can i do now?

---

### Post by sanderd17 on 2011-08-21
> **flo1805 said:**
> ok. thanks. and what can i do now?

run libreoffice as root and follow that bug report

---

### Post by flo1805 on 2011-08-21
ok...

---

### Post by sanderd17 on 2011-08-21
> **flo1805 said:**
> ok...

There is a reaction, could you do what Christopher M. Penalver said?

---

### Post by flo1805 on 2011-08-21
> please execute the following command, as it will automatically gather debugging information, in a terminal:
apport-collect 830481

```
apport-collect 830481

```

gives:


You are not the reporter or subscriber of this problem report, or the report is a duplicate or already closed.

Please create a new report using "apport-bug".

> Now open your file manager, navigate to your /var/crash directory and open the crash report you wish to submit.

the directory is empty

> If this fails you will have to open a terminal and file your report with 'ubuntu-bug /var/crash/_my_crash_report.crash' where _my_crash_report.crash  is the crash you would like to report. If you get an error that you  aren't allowed to access this report you will have to file it with 'sudo  ubuntu-bug /var/crash/_my_crash_report.crash'.


i don't really understand what to do...sorry

---

### Post by sanderd17 on 2011-08-21
Sorry, that's because I created the bug.

use apport-bug instead. I will say that my report is a duplicate of yours.

---

### Post by flo1805 on 2011-08-21
so I have to do

```
apport-bug 830481
```

right??

---

### Post by sanderd17 on 2011-08-21
no, without the numbers. just

```

apport-bug

```

That should guide you to launchpad.

---

### Post by flo1805 on 2011-08-21
so ok. I did a

```
apport-bug libreoffice
```

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/830658](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/830658)

---

### Post by jdb on 2011-08-21
What happens if you run the libreoffice binary directly like this:
```
/usr/lib/libreoffice/program/oosplash.bin
```

It will be a little crippled if it does open, but if it does,
it will help narrow down where the problem is.

jdb

---

### Post by jdb on 2011-08-21
One more thing to look at.
openoffice/libreoffice is written mostly in C++ but there are some Java components.

I think com::sun::star::uno::RuntimeException is a Java runtime error.
My runtime environment is IcedTea that comes with Ubuntu,
you might check & see if that's what you have.```
19:47:23 ~ java -version
java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

```

jdb

---

### Post by flo1805 on 2011-08-22
so, now I reinstalld my Ubuntu and did the following:

```
florian@inspiron:~$ libreoffice 
javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package libreoffice-java-common
is installed.
If it is already installed then try removing ~/.libreoffice/3/user/config/javasettings_Linux_*.xml
florian@inspiron:~$ java -version
The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-6-jre-headless
Try: sudo apt-get install <selected package>
florian@inspiron:~$ sudo apt-get install sun-java6-
sun-java6-bin     sun-java6-fonts   sun-java6-jdk     sun-java6-plugin
sun-java6-demo    sun-java6-javadb  sun-java6-jre     sun-java6-source
florian@inspiron:~$ sudo apt-get install sun-java6-jdk sun-java6-source sun-java6-demo sun-java6-fonts sun-java6-plugin 
[sudo] password for florian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gsfonts-x11 java-common odbcinst odbcinst1debian2 sun-java6-bin
  sun-java6-jre unixodbc
Suggested packages:
  default-jre equivs default-jdk-doc ttf-kochi-gothic ttf-sazanami-gothic
  ttf-kochi-mincho ttf-sazanami-mincho ttf-arphic-uming libmyodbc
  odbc-postgresql tdsodbc unixodbc-bin
The following NEW packages will be installed:
  gsfonts-x11 java-common odbcinst odbcinst1debian2 sun-java6-bin
  sun-java6-demo sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
  sun-java6-source unixodbc
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 85.9 MB of archives.
After this operation, 213 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ natty/partner sun-java6-jre all 6.26-1natty1 [6,371 kB]
Get:2 http://de.archive.ubuntu.com/ubuntu/ natty/main java-common all 0.40ubuntu1 [62.8 kB]
Get:3 http://de.archive.ubuntu.com/ubuntu/ natty/main odbcinst amd64 2.2.14p2-2ubuntu1 [13.3 kB]
Get:4 http://de.archive.ubuntu.com/ubuntu/ natty/main odbcinst1debian2 amd64 2.2.14p2-2ubuntu1 [52.1 kB]
Get:5 http://de.archive.ubuntu.com/ubuntu/ natty/main unixodbc amd64 2.2.14p2-2ubuntu1 [244 kB]
Get:6 http://de.archive.ubuntu.com/ubuntu/ natty/main gsfonts-x11 all 0.21 [10.5 kB]
Get:7 http://archive.canonical.com/ubuntu/ natty/partner sun-java6-bin amd64 6.26-1natty1 [28.7 MB]
Get:8 http://archive.canonical.com/ubuntu/ natty/partner sun-java6-jdk amd64 6.26-1natty1 [20.4 MB]
Get:9 http://archive.canonical.com/ubuntu/ natty/partner sun-java6-demo amd64 6.26-1natty1 [12.1 MB]
Get:10 http://archive.canonical.com/ubuntu/ natty/partner sun-java6-fonts all 6.26-1natty1 [1,872 B]
Get:11 http://archive.canonical.com/ubuntu/ natty/partner sun-java6-plugin amd64 6.26-1natty1 [1,866 B]
Get:12 http://archive.canonical.com/ubuntu/ natty/partner sun-java6-source all 6.26-1natty1 [17.9 MB]
Fetched 85.9 MB in 1min 58s (724 kB/s)                                         
Preconfiguring packages ...
Selecting previously deselected package java-common.
(Reading database ... 156263 files and directories currently installed.)
Unpacking java-common (from .../java-common_0.40ubuntu1_all.deb) ...
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6.26-1natty1_all.deb) ...
Selecting previously deselected package odbcinst.
Unpacking odbcinst (from .../odbcinst_2.2.14p2-2ubuntu1_amd64.deb) ...
Selecting previously deselected package odbcinst1debian2.
Unpacking odbcinst1debian2 (from .../odbcinst1debian2_2.2.14p2-2ubuntu1_amd64.deb) ...
Selecting previously deselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.14p2-2ubuntu1_amd64.deb) ...
Selecting previously deselected package sun-java6-bin.
Unpacking sun-java6-bin (from .../sun-java6-bin_6.26-1natty1_amd64.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-jdk.
Unpacking sun-java6-jdk (from .../sun-java6-jdk_6.26-1natty1_amd64.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package gsfonts-x11.
Unpacking gsfonts-x11 (from .../gsfonts-x11_0.21_all.deb) ...
Selecting previously deselected package sun-java6-demo.
Unpacking sun-java6-demo (from .../sun-java6-demo_6.26-1natty1_amd64.deb) ...
Selecting previously deselected package sun-java6-fonts.
Unpacking sun-java6-fonts (from .../sun-java6-fonts_6.26-1natty1_all.deb) ...
Selecting previously deselected package sun-java6-plugin.
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6.26-1natty1_amd64.deb) ...
Selecting previously deselected package sun-java6-source.
Unpacking sun-java6-source (from .../sun-java6-source_6.26-1natty1_all.deb) ...
Processing triggers for doc-base ...
Processing 3 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for fontconfig ...
Processing triggers for python-support ...
Setting up java-common (0.40ubuntu1) ...
Setting up gsfonts-x11 (0.21) ...
Setting up odbcinst (2.2.14p2-2ubuntu1) ...
Setting up odbcinst1debian2 (2.2.14p2-2ubuntu1) ...
Setting up unixodbc (2.2.14p2-2ubuntu1) ...
Setting up sun-java6-jre (6.26-1natty1) ...
Setting up sun-java6-fonts (6.26-1natty1) ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-lucida
Setting up sun-java6-bin (6.26-1natty1) ...
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/ControlPanel to provide /usr/bin/ControlPanel (ControlPanel) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/java to provide /usr/bin/java (java) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/java_vm to provide /usr/bin/java_vm (java_vm) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/javaws to provide /usr/bin/javaws (javaws) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/jcontrol to provide /usr/bin/jcontrol (jcontrol) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/keytool to provide /usr/bin/keytool (keytool) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/pack200 to provide /usr/bin/pack200 (pack200) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/policytool to provide /usr/bin/policytool (policytool) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/rmid to provide /usr/bin/rmid (rmid) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/rmiregistry to provide /usr/bin/rmiregistry (rmiregistry) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/unpack200 to provide /usr/bin/unpack200 (unpack200) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/orbd to provide /usr/bin/orbd (orbd) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/servertool to provide /usr/bin/servertool (servertool) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/tnameserv to provide /usr/bin/tnameserv (tnameserv) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/lib/jexec to provide /usr/bin/jexec (jexec) in auto mode.
Setting up sun-java6-jdk (6.26-1natty1) ...
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/HtmlConverter to provide /usr/bin/HtmlConverter (HtmlConverter) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/appletviewer to provide /usr/bin/appletviewer (appletviewer) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/apt to provide /usr/bin/apt (apt) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/extcheck to provide /usr/bin/extcheck (extcheck) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/idlj to provide /usr/bin/idlj (idlj) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jar to provide /usr/bin/jar (jar) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jarsigner to provide /usr/bin/jarsigner (jarsigner) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/javac to provide /usr/bin/javac (javac) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/javadoc to provide /usr/bin/javadoc (javadoc) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/javah to provide /usr/bin/javah (javah) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/javap to provide /usr/bin/javap (javap) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jconsole to provide /usr/bin/jconsole (jconsole) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jdb to provide /usr/bin/jdb (jdb) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jhat to provide /usr/bin/jhat (jhat) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jinfo to provide /usr/bin/jinfo (jinfo) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jmap to provide /usr/bin/jmap (jmap) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jps to provide /usr/bin/jps (jps) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jrunscript to provide /usr/bin/jrunscript (jrunscript) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jsadebugd to provide /usr/bin/jsadebugd (jsadebugd) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jstack to provide /usr/bin/jstack (jstack) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jstat to provide /usr/bin/jstat (jstat) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jstatd to provide /usr/bin/jstatd (jstatd) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/native2ascii to provide /usr/bin/native2ascii (native2ascii) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/rmic to provide /usr/bin/rmic (rmic) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/schemagen to provide /usr/bin/schemagen (schemagen) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/serialver to provide /usr/bin/serialver (serialver) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/wsgen to provide /usr/bin/wsgen (wsgen) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/wsimport to provide /usr/bin/wsimport (wsimport) in auto mode.
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/xjc to provide /usr/bin/xjc (xjc) in auto mode.
Setting up sun-java6-demo (6.26-1natty1) ...
Setting up sun-java6-plugin (6.26-1natty1) ...
Setting up sun-java6-source (6.26-1natty1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
florian@inspiron:~$ libreoffice 
florian@inspiron:~$ sudo rm .libreoffice/3/user/config/javasettings_Linux_X86_64.xml
florian@inspiron:~$ libreoffice 
florian@inspiron:~$ 

```and every time I start libreoffice, I got the following error message:

The application cannot be started.  A general error occurred while accessing your central configuration.

deleting the ~.libreoffice/ has no impact.

---

### Post by jdb on 2011-08-23
I burned the latest Ubuntu CD, Ubuntu-11.04-desktop-i386.iso, 
and booted to it.
Sure enough no Java was installed.
But, libreoffice was installed and it worked fine.
It must contain enough runtime Java to get by ?????

Have you tried running labreoffice from a live CD?
If that works, I can't imagine why it wouldn't work with a fresh install of Ubuntu.

If that doesn't work, it may be something in your bios ???

If you ever get this solved let us know what you found.

jdb

---

### Post by flo1805 on 2011-08-24
I have a suspicion.

When I reinstalled my Ubuntu, I always chose "erase Ubuntu 11.04 and reinstall". 
Maybe it's better to format the partition Ubuntu is on and to install it new.
Maybe if I choose the option reinstall, not everything will really be new installed (maybe some parts of the file system will not be erased).
Could that be, or am I wrong?

---

### Post by jdb on 2011-08-24
> **flo1805 said:**
> I have a suspicion.

When I reinstalled my Ubuntu, I always chose "erase Ubuntu 11.04 and reinstall". 
Maybe it's better to format the partition Ubuntu is on and to install it new.
Maybe if I choose the option reinstall, not everything will really be new installed (maybe some parts of the file system will not be erased).
Could that be, or am I wrong?

I don't know, but you might be on to something.
It might not be erasing your home directory or some
other config files.

If you have stuff stored in your home directory you should
back that up first, but don't re-use the config directories that
start with a "." , the ones you have to us "ls -a" to see.


Does it work when you boot to a liveCD??

jdb

---

### Post by flo1805 on 2011-08-25
so now I solved the problem.

I just reinstalld Ubuntu with the partiton table...now it works fine.
I hope someone will someday find out how to fix this problem without reinstalling th os.

Thank you for all your help and time :)

---

### Post by flo1805 on 2011-08-25
what a ****....

it doesn't work...
I installed sun-java6 and it works fine. I did a reboot and it doesn't work any more...

---

### Post by sanderd17 on 2011-08-25
> **flo1805 said:**
> what a ****....

it doesn't work...
I installed sun-java6 and it works fine. I did a reboot and it doesn't work any more...

You are driving me nuts

Can you build the development version of libreoffice? [http://www.documentfoundation.org/develop/](http://www.documentfoundation.org/develop/)

---

### Post by fgi on 2012-05-10
Hi,

Felt in the same problem tonight after an upgrade from ocelot to pangolin. After installing, cleaning, purging, reinstalling debs from website, copying profiles from another working user and almost hanged myself, I "straced" the application and found that you only have to remove the .ure folder in you home (nice permission denied on some file in there).

Now it works.

---

### Post by vincebs on 2012-09-09
I had this problem and I fixed it by typing in the following:
```
sudo chown -vR myusername ~/.config
```

Apparently it's a permissions issue with the .config directory. You could also try granting write access to this folder and its subdirectories

---

