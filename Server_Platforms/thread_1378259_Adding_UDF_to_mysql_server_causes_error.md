---
title: "Adding UDF to mysql server causes error"
date: 2010-01-11
forum: Server Platforms
---

### Post by johndunne on 2010-01-11
Hi,

I'm running Ubuntu 9.10 (x86_64) with the latest server and client versions currently available: 5.1.37-1ubuntu5. I'm trying to add a UDF to mysql server but get the following error:
ERROR 1126 (HY000): Can't open shared library 'distance.so' (errno: 22 /usr/lib/mysql/plugin/distance.so: failed to map segment from shared object: Permission denied)
  
when I call the following command to add the function to mysql:

 CREATE FUNCTION distance RETURNS INT soname "distance.so";

The function I'm adding is called distance (in distance.c), and is the following:
```

/*

#############################################################################
# Header from the template:
#
# http://dev.mysql.com/sources/doxygen/mysql-5.1/udf__example_8c-source.html
#############################################################################
*/

#ifdef HAVE_DLOPEN

my_bool distance_init(UDF_INIT *initid, UDF_ARGS *args, char *message);
longlong distance(UDF_INIT *initid, UDF_ARGS *args, char *is_null,
                    char *error);
longlong distance(UDF_INIT *initid __attribute__((unused)), UDF_ARGS *args,
                    char *is_null __attribute__((unused)),
                    char *error __attribute__((unused)))

{
  if (args->arg_count != 2)
    return -3;

  if (args->arg_type[0] !=  STRING_RESULT)
    return -1;

  if (args->arg_type[1] !=  STRING_RESULT)
    return -2;

  const char *wA = args->args[0];
  const char *wB = args->args[1];
  int m = args->lengths[0];
  int n = args->lengths[1];
  int cost =0;
  int i;
  int j;
  longlong D[(m+1)][(n+1)];

  for (i = 0; i <= m; i++){
    D[i][0] = i;
  }

  for (i = 1; i <= n; i++){
    D[0][i] = i;
  }

 

  for (i = 1; i <= m; i++){
    for (j = 1; j <= n; j++){
      if (wA[i-1] == wB[j-1])
        cost = 0;
      else
        cost = 1;

      if ((D[i-1][j] + 1 <= D[i][j-1] + 1) && (D[i-1][j] + 1 <= D[i-1][j-1] + cost)){ // min(D[i-1][j]+1)
        D[i][j] = D[i-1][j] + 1;
      }
      else{
        if ((D[i][j-1] + 1 <= D[i-1][j] + 1) && (D[i][j-1] + 1 <= D[i-1][j-1] + cost))  { // min(D[i][j-1]+1
          D[i][j] = D[i][j-1] + 1;
        }
        else{
           D[i][j] = D[i-1][j-1] + cost;                                                // min(D[i-1][j-1]+1
        }
      }
    }
  }

  return D[m][n];
}

my_bool distance_init(UDF_INIT *initid __attribute__((unused)),
                        UDF_ARGS *args __attribute__((unused)),
                        char *message __attribute__((unused)))

{
  return 0;
}
#endif

```and I build the so using the following command:
   gcc -shared -I/usr/include/mysql/ -fPIC -o /usr/lib/mysql/plugin/distance.so distance.c

The include files are the correct version for the mysql biniaries I have. I'm unable to fund any information regarding the error printed hence my plea for assistance! 

Any help is greatly appreciated!

---

### Post by johndunne on 2010-01-12
Anyone have an idea :popcorn:

---

### Post by BkkBonanza on 2010-01-12
It says something about permissions. According to the docs the user calling CREATE FUNCTION needs to have INSERT privileges. Not sure if that's it but worth checking. Also make sure file permissions on the distance.so are going to allow mysql user to load it.

---

### Post by johndunne on 2010-01-13
Hi BkkBonaza, thanks for taking the time to help - I've added the function as root user and still no luck :( In the meantime, I've moved the database off to a centos platform while I figure this out. The UDF was added to that db without any issues. Strange.

---

