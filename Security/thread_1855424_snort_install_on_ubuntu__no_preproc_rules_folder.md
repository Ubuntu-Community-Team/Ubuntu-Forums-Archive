---
title: "snort install on ubuntu : no preproc rules folder"
date: 2011-10-06
forum: Security
---

### Post by nkd on 2011-10-06
hi everyone,
I am trying out a snort installation on my ubuntu (10.10)machine. I checked out the rules in the directory /etc/snort/rules , they seem to be all there. But I donot have a preproc_rules directory or a so_rules directory. Aren't these needed ? Becoz, my snort.conf file has the relevant entries for both of them.

BTW the rules directory and the rules in it were part of the apt-get install of the snort. I didnot download them from the snort website separately and install them.

I am wondering if the pre-processor is working at all without the rules in the preproc directory ?!?!?

Thanks in advance for any help or suggestions.

nishith

---

### Post by unspawn on 2011-10-06
> **nkd said:**
> But I donot have a preproc_rules directory or a so_rules directory.
Preprocs are in the "snort-common-libraries" package.


> **nkd said:**
> BTW the rules directory and the rules in it were part of the apt-get install of the snort. 
Dependencies may get installed automagically but rules are in the "snort-rules-default" package.


> **nkd said:**
> I didnot download them from the snort website separately and install them.
You should update them. If you use Snort rules use Oinkmaster or else see the Emerging Threats site for details.


> **nkd said:**
> I am wondering if the pre-processor is working at all without the rules in the preproc directory ?!?!?
Snort comes with multiple preprocessors (see the "snort-doc" package). Some, like http_inspect or sfportscan may work but others like SSH/SSL may not w/o preloading dynamic preprocessor libraries.


BTW this doesn't seem a security flaws/updates/notices discussion to me but a configuration issue (and a failure to read the most basic of docs IMHO)...

---

