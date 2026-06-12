---
title: "PHP5 mySQL problem"
date: 2006-03-06
forum: Server Platforms
---

### Post by SickBoy on 2006-03-06
When I try to connect to a mysql database I keep getting the error.; Call to undefined function mysql_connect()

I've checked /etc/php5/apache2/php.ini and I have uncommented the line 

extension=mysql.so 

Also I have installed packages php5, php5-mysql. 

phpinfo() returns that php is compiles with mySQL support.

The odd thing is that phpMyAdmin works perfectly and I can connect to a mySQL database I have.

The code that gives the error is:

```

$servidor = "localhost";
$nombre_usuario = "";
$contrasenya ="";

$tipo = "mySQL";

    switch ($this->tipo) {
      case "MSSQL":
        $this->conexion = mssql_connect ( $servidor, $nombre_usuario, $contrasenya );
        break;
      case "mySQL":
        $this->conexion = mysql_connect ( $servidor, $nombre_usuario, $contrasenya );
        break;
    }

```

And the error is

```

Fatal error: Call to undefined function mysql_connect() in /var/www/generaFichero/database.php on line 23

```

I'm under Breezy

Thanks in advance.

---

### Post by jmilster on 2006-03-06
I haven't installed PHP and MySQL on Ubuntu yet, but I know that in Windows and Fedora Core 4 I had to also download the MySQL .dlls for PHP and put them into the php/ext directory.

---

### Post by madubuntuer on 2006-03-06
yes that is very true because from php5 on wards the mysql libraries are no longer bundled with php hence u go to the developers section on mysql.org to obtain them.

---

### Post by transactionlogfiller on 2006-03-06
You can just apt-get install php5-mysql

---

