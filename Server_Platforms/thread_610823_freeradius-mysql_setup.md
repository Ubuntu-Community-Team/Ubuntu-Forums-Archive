---
title: "freeradius-mysql setup"
date: 2007-11-12
forum: Server Platforms
---

### Post by ohp on 2007-11-12
I suspect I'm just being dense here, but I'm looking to provide a central mechanism for authenticating people across a large number of services. I thought I'd try freeradius, with a mysql backend.

I've installed the packages freeradius, and freeradius-mysql

this is as far as I've got! the installers havn't configured a schema in mysql, and looking for a schema script installed as part of the above packages, I'm drawing a blank. 

So I'm having a problem locating the next step in the instructions.  dpkg configure tells me that both of the above packages are installed and configured.

Looking on the web, people seem to either magic their own schema out of nowhere, or use the one that comes in the source tarball (db_mysql.sql).

Do I have to use the sql from the original source tarball? seems a bit odd to me that this doesn't come with the binary packages.

I'm sure I'm just missing something really obvious though.

---

### Post by ohp on 2007-11-13
From the lack of responses, to this query, I concluded that I was probably missing something so obvious it wasn't worth anyone telling me what it was!

it appears that the file RADIUS-SQL.schema file is misleading when it points at src/modules/rlm_sql/drivers/rlm_sql_mysql/db_mysql.sql as the source of the schema, when it's actually included as examples/db_mysql.sql.gz

I think I might document this install in a howto

---

### Post by mcnaughty80 on 2007-11-16
Hi,

I've been doing the same as you with the freeradius and freeradius-mysql, i found setting up mysql a little bit of a headache at first, most of the setup notes i read from the mysql site, after getting that setup (hours later cuz i didn't know what i was doing at first) sql is not all that hard once i learned the commands. still working on setting up freeradius, the guide i found here seems me to be different then the files we can download from the synaptic package manager, when configuring radiusd.conf there has been changes made to this file that don't match what is in the forums here... also after i do get the files configured right by crash coursing, i'll be adding a PPPoE server on the same server... i'm looking to use this server to manage a wireless isp AP's...

once i have figured things out a little more i'll try and post what i have come accross using these packages...

---

### Post by vermin on 2007-12-16
Hi I am very new to linux but need a radius server, seem to have installed everything but cant seem to find the dialup admin - do you know of a step by step guide or any advice as what to install - very new - Thanks for your time

---

### Post by dbrower256 on 2008-01-25
I am insterested in a step-by-step set of instructions for setting up freeradius to use with mysql also.  I hope you will post what you learn.

Daniel

---

### Post by dbrower256 on 2008-01-25
I posted again to set an email notification to me.

---

### Post by chk9 on 2008-02-01
> **dbrower256 said:**
> I posted again to set an email notification to me.

Will setup freeradius for cisco dev. identification. Will follow this thread as well with great interest!

HF, Chris.

---

### Post by dbrower256 on 2008-02-04
> **chk9 said:**
> Will setup freeradius for cisco dev. identification. Will follow this thread as well with great interest!

HF, Chris.

What?

---

