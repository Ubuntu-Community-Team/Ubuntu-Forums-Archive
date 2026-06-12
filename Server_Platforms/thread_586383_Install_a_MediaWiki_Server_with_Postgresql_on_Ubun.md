---
title: "Install a MediaWiki Server with Postgresql on Ubuntu"
date: 2007-10-22
forum: Server Platforms
---

### Post by experience on 2007-10-22
I followed the instructions and I have already a accessible MediaWiki for the Last steps -- specify the mediaWiki name, sysadmin user, including the the postgresql database settings. I leave most of them the default values. Then I click Install MediaWiki.

then I got the errer message:

Generating configuration file...
# Database type: PostgreSQL
# Loading class: DatabasePostgres
# Attempting to connect to database "wikidb" as "wikiuser"...
# Checking the version of Postgres...version 8.2 is OK.
# Checking for tsearch2 in the schema "public"...FAILED. Make sure tsearch2 is installed. See this article for instructions.

But actually I already have the postgresql-contrib-8.2 installed.

Do I need some more steps to setup the environment to work?

I am using the AMD 64 bit version of Ubuntu.

---

### Post by davidomundo on 2008-01-30
I see that you asked this question 3 months ago, but in case you still haven't figured it out (and for others looking for the answer):

You have to make your database tsearch2-ified and not just install the contrib packages.

So from your state, you do:
```

cd /usr/share/postgresql/8.2/contrib/
sudo -u postgres psql wikidb < tsearch2.sql
sudo -u postgres createlang plpgsql wikivs

```

and then give permission to the newly generated tsearch2 tables to wikiuser.

---

### Post by erkswede on 2008-02-11
> sudo -u postgres createlang plpgsql wikivs

should be *wikidb* at the end right?

---

### Post by saibatizoku on 2008-03-20
According to this site:

[http://www.mediawiki.org/wiki/Manual:Installing_MediaWiki#Postgres](http://www.mediawiki.org/wiki/Manual:Installing_MediaWiki#Postgres)

it should be

```
sudo -u postgres createlang plpgsql wikidb
```

:)

I believe the general idea is to add a new procedural language to the database.

Check out this link:

[http://www.postgresql.org/docs/8.2/static/app-createlang.html](http://www.postgresql.org/docs/8.2/static/app-createlang.html)

---

