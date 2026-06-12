---
title: "trying to run test with pgbench-tools on ubuntu server and postgresql"
date: 2014-12-30
forum: Server Platforms
---

### Post by cesar15 on 2014-12-30
Hello, I´ve installed postgresql 9.1 on ubuntu 12.04 with pgpoolII-3.3.3 and pgPoolAdmin.

I´m trying to make a test with pgbench-tools to measure the performance of postgresql.

So I move to the directory where is pgbench-tools and configure the config file.

I try to execute this order:

sudo -u postgres ./runset

After this it appears a message "Removing old pgbench tables"

First error message (seems not to be important) is: ERROR: table "accounts does not exist"

After this it appears a message: VACUUM creating new pgbench tables

After this 

creating tables
10000 tuples done
20000 tuples done
...
100000 tuples done
...
vacuum...done.
Run set #1 of 2 with 2 clients scale=1
Running tests using: psql -h localhost -U postgres -p 5432 pgbench
Storing results using: psql -h localhost -U postgres -p 5432 pgbench

And after this it comes "the crash":

ERROR: relation "branches" does not exist
LINE 1: select count(*) for branches
ERROR: Attempt to determine database scale returned "", aborting

it´s maybe and stupid issue and I´m not being able to solve it as i don´t have a high level of knowledge on those systems.

Any idea about what to try?

---

### Post by cesar15 on 2015-01-01
Solved: the tables "accounts" and "branches" refer to the table names in pgbench shipped with Postgres 8.3 and older. It has been changed to pgbench_* after that. So I was facing a version mismatch of pgbench-tools. Solved after downloading pgbench tools from github [https://github.com/gregs1104/pgbench-tools](https://github.com/gregs1104/pgbench-tools)

---

