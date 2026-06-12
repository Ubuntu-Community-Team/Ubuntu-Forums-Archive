---
title: "Hi I am trying to get Mifos up and running form mifos.org"
date: 2012-01-08
forum: Server Platforms
---

### Post by frankjath on 2012-01-08
create production tables
In the directory where you unpacked the archive, do:

mysql -D mifos -u mifos -pmifos < db/sql/base-schema.sql
mysql -D mifos -u mifos -pmifos < db/sql/base-data.sql
mysql -D mifos -u mifos -pmifos < db/sql/init_mifos_password.sql

What exactly is it asking me to do?

When I connect to the database "mysql -D mifos -u mifos -pmifos" and then past "< db/sql/base-schema.sql" it gives me.

< db/sql/base-schema.sql
    ->

Where do I go from here? Help would be much appreciated.

---

