---
title: "trying to insert JPG file into a mysql table"
date: 2011-03-12
forum: Server Platforms
---

### Post by yanvolking on 2011-03-12
Hello community,

I would like to store JPG files in a mysql database table.  I figured that using BLOB fields on the one hand and the 'load_file' command on the other would do the trick.

Here is how I set up the table:

mysql> create table blobtable (id int(10) not null auto_increment, fileName varchar(15) not null, file      longblob not null, primary key(id) );

Query OK, 0 rows affected (0.51 sec)

then I tried to enter the data:

mysql> insert into blobtable(filename,file)values('pic',load_file('/var/www/temp/IMGP4764.JPG'));

which got me the following error signal:
ERROR 1048 (23000): Column 'file' cannot be null

It seems to me that the file path to the JPG file (although correct) is the source of the problem, and is causing  the load_file command not to work.

My first attempt was with the JPG file in my PC's home directory.  When that returned the same error message, I figured that maybe the file had to be in the PC's (server's) web area so I put it under the 'www' directory.  But obviously it was not the solution.

Any ideas what I should do?

Thanks in advance

---

### Post by SeijiSensei on 2011-03-12
If you using MySQL to support a web application, I'd store only the image URLs in the database and put the images themselves in the appropriate location in the file system.

---

### Post by BkkBonanza on 2011-03-12
Your table has 4 cols and they are "not null". But your insert has only 2 cols. So the two unspecified must be null (you don't supply a value). Hence, the error msg. You should try fully specifying each col.

I tend to agree with storing images external to the table but it should work and I don't believe your loadfile is the problem. Also, why have an auto_incr and key column seperate - usually they can be one and the same. For the auto_incr column you need to insert a 0 to fill the column and it will generate the next value.

insert into blobtable values(0, 'pic', load_file('blah/blah'), 0);

---

### Post by rubylaser on 2011-03-13
+1 for just storing the path to the jpg and saving the file to the filesystem.

---

### Post by yanvolking on 2011-03-13
Hi Guys,

Thanks for your replies.  However I am still stuck.  I paid attention above all to BkkBonanza's reply as it seemed to give the quick fix to my problem.

For efficiency's sake I deleted the table and recreated it with changes :

-------------------------------------
mysql> create table blobtable (
    -> id int(10) auto_increment primary key,
    -> fileName varchar(15),
    -> file longblob
    -> );
Query OK, 0 rows affected (0.05 sec)
-------------------------------------

then I entered the data :

--------------------------------------
mysql> insert into blobtable (fileName, file) values ('pic', load_file('/home/yan/temp1/apo.jpg'));
Query OK, 1 row affected (0.00 sec)
--------------------------------------

as id is auto_increment, I left it alone.  In any case the data entry sequence returned no error but when I checked the table content, i got :

---------------------------------------
mysql> select * from blobtable;
+----+----------+------+
| id | fileName | file |
+----+----------+------+
|  1 | pic      | NULL |
+----+----------+------+
1 row in set (0.00 sec)
-----------------------------------------

so although the data entry sequence returned no error, the jpg file was not entered (NULL in the file field).
I have checked and double checked the path to the jpg file and I am sure it is '/home/yan/temp1/apo.jpg'.

Any further suggestions would be greatly welcome.....

Thanks again in advance for your help.

Yan

---

### Post by rubylaser on 2011-03-13
You may want to look here for some of the reasons against doing this
[http://www.freeopenbook.com/mysqlcookbook/mysqlckbk-chp-17-sect-7.html]("http://www.freeopenbook.com/mysqlcookbook/mysqlckbk-chp-17-sect-7.html")

But, your syntax looks okay...
Here's s relevant section from that link.  Does your file satisfy the conditions it mentions?
> The LOAD_FILE( ) function takes an argument indicating a file to be read and stored in the database. For example, an image stored in /tmp/myimage.png might be loaded into a table like this:

mysql> INSERT INTO mytbl (image_data) VALUES(LOAD_FILE('/tmp/myimage.png'));
To load images into MySQL with LOAD_FILE( ), certain requirements must be satisfied:

[B]The image file must be located on the MySQL server host.

The file must be readable by the server.

You must have the FILE privilege[/B]

---

### Post by yanvolking on 2011-03-14
Hello again,

Thanks rubylaser for your reply. But it is still returning NULL in the "file" field.

Going through your latest reply point by point:

1) [B]The image file must be located on the MySQL server host.
[/B]I am working on a stand-alone PC in localhost mode (ie everything is happening on my hard disk).   The FULL path of the jpg file is :
         /home/yan/temp1/apo.jpg

MYSQL is installed in /etc/mysql/

I therefore imagine that this situation satisfies the above condition (?).

2) [B]The file must be readable by the server.
[/B]ls -l / /home/yan/temp1/apo.jpg returns :
         -rwxrwxrwx 1 yan yan 65261 2011-03-01 10:08 /home/yan/temp1/apo.jpg
so the file is readable at all levels.  Is there perhaps a special setting somewhere for the server to read file?

3)** You must have the FILE privilege**

I am working as root so I should have all the privileges activated.  To double check I ran :

mysql> show grants for root@localhost;
+----------------------------------------------------------------------------------------------------------------------------------------+
| Grants for root@localhost                                                                                                              |
+----------------------------------------------------------------------------------------------------------------------------------------+
| GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' IDENTIFIED BY PASSWORD '*D8B363E74C711A6ECC83FA15D61FDA03B6722265' WITH GRANT OPTION |
+----------------------------------------------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)
This effectively confirms de-facto that I have file privileges amongst others.

SO this seems to be a tough one.  Perhaps someone could do this same exercise on their localhost machine (using any other jpg file) and see if it loads into the database.

Thanks in advance again for any help.....

Yan

---

### Post by BkkBonanza on 2011-03-14
Be sure to check mysql.err for any related or unusual messages... sometimes something is there indicating the problem.

---

