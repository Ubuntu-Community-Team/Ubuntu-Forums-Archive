---
title: "how to run ADempiere server in background startup services at boot time"
date: 2009-11-12
forum: Server Platforms
---

### Post by mady03sam on 2009-11-12
[SIZE=3]hi,
    im unable resolve dis issue regardin how to RUN ADempiere server at boot time in backgroun services.............. it shuld run in background, 

created a bashscript in /etc/init.d to run ADempiere server wen i restart ma UBUNTU9.04 SERVER so i succesd in makin a bash scrpit to run, but after startin ma PC it starts services and ma ADempiere server, so after dat im unable to access ma DESKTOP(GUI), even unable to go further. so tell me how to resolve dis issue............ [/SIZE]

---

### Post by croo on 2009-11-12
try creating a symbolic link to the new adempiere script in the relevant RC_.d directory.  For example by default I think ubuntu boots into init 2 (though that might differ for the server version?) so in RC2.d make a link with something like
# ln -s /etc/init.d/yourAdempiereScriptNameHere S99adempiere

---

### Post by mady03sam on 2009-11-13
but the script shud be running in background is it possible wid dis command...................like postgresql n another services it shud be started at boot time n after i need to run GUI without any issues is dat possible CROO

---

### Post by plavania on 2010-06-15
Please visit the Blog section of Walking Tree on "How To's" of Adempiere. Walking Tree has extensive experience in Adempiere and built there own ERP product EagleRP on top of Adempiere. They have a strong presence in ERP Implementation and Customizations around Adempiere, for more than 4 years now with a clientele from different verticals. By end of 2010, the company is publishing a book on "How To's" for Adempiere to make life easier for all fellow implementers.
Incase you do not find the information that you are looking for already existing on their blog, try posting a question, and you can be assured of a prompt and overwhelming reply.
[http://www.walkingtree.in](http://www.walkingtree.in)
[http://wtcindia.wordpress.com/](http://wtcindia.wordpress.com/)

---

