---
title: "webmin and postgresql on Ubuntu Server"
date: 2009-01-19
forum: Server Platforms
---

### Post by bigbearomaha on 2009-01-19
I have ubuntu server 8.04 setup with webmin installed as well.

after installing postgresql, I am able to initially start and access the database, even create a database, just fine.

When attempting to "execute' sql command from a script for a certain webapp ( opensis 4.2) it will not allow the user postgres to authenticate. in order to carry out the execution of the .sql file.

I have seen where there is some issue with how authentication is setup in a few threads an on the web. I am not sure however that simply changing the authentication method to trust or md5 as the few I have done both and had no success ( yes,  I did restart postgres after each time ).

is it a matter of just creating a superuser acct and changing the file in the webapp to use that new username to access the db?

What of the default user "postgres"?  I thought the default pass was blank for that user so from a fresh install, authentication shouldn't be an issue should it?

any suggestions accepted.

Big Bear

---

