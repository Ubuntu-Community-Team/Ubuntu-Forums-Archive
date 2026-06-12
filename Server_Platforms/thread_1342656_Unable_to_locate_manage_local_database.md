---
title: "Unable to locate/ manage local database"
date: 2009-12-01
forum: Server Platforms
---

### Post by sptrsn on 2009-12-01
I am successfully running Xampp 1.7 on Ubuntu 8.10. 
I am also successfully running SugarCRM on said machine. 

Everything appears to be completely normal, EXCEPT...
in PHP MyAdmin, the database is not listed in the left column with other databases. If I turn off mysql from the Xampp control panel, CRM stops working. It all seems right, except that I can't get to the database to manage the database. 

I did have some problems with an earlier attempt at installing WAMP, but abandoned that and decided to learn how to use and configure Xampp. 

Is it possible to have two mysql database engines running at the same time?
If so, how would I access the previous one since all references to WAMP are gone?

Sure appreciate any thoughts or ideas. Thanks.

---

### Post by rudy.b on 2009-12-01
It is possible to have more than one MySQL servers running, but they'd have to be listening on different ports.  So that's unlikely unless you explicitly set up one of your MySQL instances to listen to a non-standard port (you can verify this by executing 'sudo netstat -plnt' and check how many instances of mysqld are running).

Do you have multiple users in your database?  Are you logging into PHPMyAdmin as root?

---

### Post by sptrsn on 2009-12-01
Thank you rudy.b. Logging in as root in PMA made the other database show up. 
I had recently run the security routine to set all the passwords and it didn't even occur to me that I had been logging in under a different user profile. 
Thanks again.

---

### Post by rudy.b on 2009-12-01
Cool, glad to help.  O:)

You should be able to update the privileges of all your other users from root in PHPMyAdmin if that's important.

---

