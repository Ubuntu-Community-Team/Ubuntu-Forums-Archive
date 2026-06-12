---
title: "Apache Web Server"
date: 2013-03-29
forum: Server Platforms
---

### Post by bellygrevios on 2013-03-29
Hi everyone,
So recently I've been trying to make my own webserver (I have the basics set up now). My friend has his server set up so when you send a HTTP GET request to it the server turns it into a SQL query and returns all the data from that row as a JSON file. So the request would be somewebsite.com/something?=a%20SQL%20query. Does anyone have any clue how he   did it?
Thanks
Ubuntu Server Edition 12.04 (LTS)

---

### Post by alphacrucis2 on 2013-03-29
Why don't you ask him?

---

### Post by bellygrevios on 2013-03-29
> **alphacrucis2 said:**
> Why don't you ask him?
So maybe friend is a bit too strong of a word... More of a person I met and briefly worked on a project with.

---

### Post by lisati on 2013-03-29
*Thread moved to **Server Platforms**.*

One way would be to have a web page written using PHP that parses the passed URL, does the necessary SQL lookup, and outputs the appropriate HTML or XML based on the results of the SQL query.

---

### Post by SeijiSensei on 2013-03-29
It's probably a PHP script.  It could be pretty insecure if he doesn't apply strong validation checks against the input string. What if the query is "drop database"?

---

### Post by mharv on 2013-03-30
I would write a program that knows just enough about HTTP to parse incoming data ,interpret as sql request, etc. Or would create a plugin that does the same thing for an existing server such as NGINX or Apache.

Using a standard PHP implementation would be extremely slow and inefficient for such a specialized and narrow purpose.

---

### Post by Cheesemill on 2013-03-31
> **SeijiSensei said:**
> It's probably a PHP script.  It could be pretty insecure if he doesn't apply strong validation checks against the input string. What if the query is "drop database"?Indeed...

[IMG]http://imgs.xkcd.com/comics/exploits_of_a_mom.png[/IMG]

---

### Post by lisati on 2013-03-31
Too true: sanity checks are essential for anything entered by URL and/or web form that will be used to query or update a database.

---

### Post by thnewguy on 2013-03-31
The concept is fairly simply, it could be done with a few lines of PHP code. However, as others have pointed out you need to make sure of two things:
1. There is no sensitive information in the database as anyone in the world will be able to access the information.
2. Do not allow the PHP script to have write/drop/delete access to the database. Make sure it has read-only access or someone will come along and erase your data.

---

