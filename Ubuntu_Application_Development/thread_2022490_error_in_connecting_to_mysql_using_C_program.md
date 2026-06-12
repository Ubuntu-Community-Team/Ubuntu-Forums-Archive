---
title: "error in connecting to mysql using C program"
date: 2012-07-11
forum: Ubuntu Application Development
---

### Post by fivestaar on 2012-07-11
Hi all

I am trying to access mysql through a c program, bt am stuck with a specific error. I have searched the net for solutions, but nothin helped

Code:

```

/* Simple C program that connects to MySQL Database server*/
#include <mysql.h>
#include <stdio.h>

main() {
  MYSQL *conn;
  MYSQL_RES *res;
  MYSQL_ROW row;

  char *server = "localhost";
  char *user = "root";
  //set the password for mysql server here 
  char *password = ""; /* set me first */
  char *database = "mysql";

  conn = mysql_init(NULL);

  /* Connect to database */
  if (!mysql_real_connect(conn, server,
        user, password, database, 0, NULL, 0)) {
      fprintf(stderr, "%s\n", mysql_error(conn));
      exit(1);
  }

  /* send SQL query */
  if (mysql_query(conn, "show tables")) {
      fprintf(stderr, "%s\n", mysql_error(conn));
      exit(1);
  }

  res = mysql_use_result(conn);

  /* output table name */
  printf("MySQL Tables in mysql database:\n");
  while ((row = mysql_fetch_row(res)) != NULL)
      printf("%s \n", row[0]);

  /* close connection */
  mysql_free_result(res);
  mysql_close(conn);
}
```

The command i used to compile the program is:
gcc -o connectsql $(mysql_config --cflags) connectsql.c $(mysql_config --libs)

Error: 
/tmp/ccx4qAGm.o: In function `main':
connectsql.c: (.text+0x13f): undefined reference to`mysql_free_results'
collect2: ld returned 1 exit status

---

### Post by spjackson on 2012-07-11
> **fivestaar said:**
> 
Error: 
/tmp/ccx4qAGm.o: In function `main':
connectsql.c: (.text+0x13f): undefined reference to`mysql_free_results'
collect2: ld returned 1 exit status
The code you have posted has mysql_free_result (singular correct) but the error message has mysql_free_results (plural incorrect). Are you sure that the code you are compiling has mysql_free_result not mysql_free_results?

---

### Post by manodo89 on 2012-07-11
[LEFT][COLOR=#000000][FONT=Arial]While you have included the mySQL header files in your code, you haven't included the mySQL library in your link options.
[internet marketing tips and strategy](http://internetmartketingpage.com/)
[effective internet marketing](http://internetmartketingpage.com/)
[/FONT][/COLOR][/LEFT]

---

### Post by fivestaar on 2012-07-12
> **spjackson said:**
> The code you have posted has mysql_free_result (singular correct) but the error message has mysql_free_results (plural incorrect). Are you sure that the code you are compiling has mysql_free_result not mysql_free_results?

@spjackson thanks for pointing that out. 
I checked my program n there were some typing errors, Helped me solve the prob. SO silly of me to over look it:oops:#-o

---

