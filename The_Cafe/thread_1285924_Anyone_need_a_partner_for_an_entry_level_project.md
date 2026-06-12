---
title: "Anyone need a partner for an entry level project?"
date: 2009-10-08
forum: The Cafe
---

### Post by blittergames on 2009-10-08
I know Linux/BSD/PHP/SQL pretty well.  I am learning python on the side.  Does anyone have any projects where they need a partner or anyone want to form a new project related to open-source?

---

### Post by scragar on 2009-10-08
Just how much PHP do you know? I'm working on a database extraction project, which does reduce efficiency somewhat, but it's designed to make it easier to move from one database to another, if that makes sense.

Example code using mysql[php]
require_once '/etc/php/sLib/core/request';
require_once '/etc/php/misc/hash'
require_once '/etc/php/sLib/databse/mysql'

$username = new s_POST('username');
$password = new s_POST('password');

$database = new s_database_mysql('localhost', 'username', 'password', 'database');
if( isset( $databse )){
  $results = $database->fetch('tableName', '*', array(
                'username'=> $username->raw,
                'password'=> md5('salt'.$password->raw.'salt')
  ))
  if($results->rows >= 1)
    echo 'Username and password match up.';
  else
    echo 'Username and password match failed.'
}else{
  echo 'Database error: '. $database->errors;
}[/php]
And that same code using ODBC on windows(changes in red):
```
require_once '[color=red]s_Lib\\core\\request[/color]';
require_once '[color=red]misc\\hash[/color]'
require_once '[color=red]sLib\\databse\\odbc[/color]'

$username = new s_POST('username');
$password = new s_POST('password');

$database = new s_database_[COLOR="Red"]odbc[/COLOR]('localhost', 'username', 'password', 'database');
if( isset( $databse )){
  $results = $database->fetch('tableName', '*', array(
                'username'=> $username->raw,
                'password'=> md5('salt'.$password->raw.'salt')
  ))
  if($results->rows >= 1)
    echo 'Username and password match up.';
  else
    echo 'Username and password match failed.'
}else{
  echo 'Database error: '. $database->errors;
}
```

So far those are the only two databases it supports, but I'm working on sqlite.
Once it supports a few more systems I'm either going to make it public or clean up the code a lot.

---

### Post by Tibuda on 2009-10-08
@scragar: have you heard of pdo? [http://php.net/pdo](http://php.net/pdo)

---

### Post by scragar on 2009-10-08
> **danielrmt said:**
> @scragar: have you heard of pdo? [http://php.net/pdo](http://php.net/pdo)

My only reason for avoiding PDO is that it's unsuitable for large database transactions in terms of ram, every select query returns a multidimentional array, and since PHPs arrays are rather large and inefficient I wanted to keep the usage of them to a minimum, my code will hold the object in whatever format the database returns it in until you ask for it.

---

### Post by keiichidono on 2009-10-08
Find something you like and work on it. You won't have fun programming things that bore you.

---

