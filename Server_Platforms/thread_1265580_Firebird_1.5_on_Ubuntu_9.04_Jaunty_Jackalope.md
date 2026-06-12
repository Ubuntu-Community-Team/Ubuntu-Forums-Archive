---
title: "Firebird 1.5 on Ubuntu 9.04 Jaunty Jackalope"
date: 2009-09-13
forum: Server Platforms
---

### Post by BioComputing on 2009-09-13
Here is how to install Firebird 1.5.5 on Ubuntu 9.04:

```
sudo apt-get install libstdc++5
```

From:
[http://www.firebirdsql.org/index.php?op=files&id=engine_155](http://www.firebirdsql.org/index.php?op=files&id=engine_155)

Download:
FirebirdSS-1.5.5.4926-0.i686.tar.gz

unpack and find postinstall.sh in firebird setup /scripts directory, open it with editor and remove -M parameter from TryAddUser() procedure:
```
TryAddUser() {

	AdditionalParameter=$1
    testStr=`grep firebird /etc/passwd`
	
    if [ -z "$testStr" ]
      then
        useradd $AdditionalParameter **[COLOR="Red"]-M[/COLOR]** -d $FBRootDir -s /bin/false \
            -c "Firebird Database Owner" -g firebird firebird 
    fi

}
```

Save&exit, now you can start install script from firebird setup directory:
```
sudo ./install.sh
```

Enter SYSDBA password when prompted and that's it. Firebird is intalled in directory:
```
/opt/firebird
```

To enable access to user defined functions (UDF's) edit firebird.conf
```
sudo nano /opt/firebird/firebird.conf
```

Uncomment and change UdfAccess to:
```

UdfAccess = Restrict /opt/firebird/UDF

```

Save&Exit. (Setting UDFAccess to "Full" doesn't work for me, maybe it's bug.)

Restart firebird:
```
sudo /etc/init.d/firebird reload
```

Now UDF's works!

To compile your UDF's written in C, chdir to directory which contains your UDF source files and compile it:
```
gcc -c <name_of_your_udf>.c
gcc <name_of_your_udf>.o -o lib<name_of_your_udf>.so -shared

```

Copy your shared object to UDF directory:
```

sudo cp ./lib<name_of_your_udf>.so /opt/firebird/UDF/lib<name_of_your_udf>.so
sudo chown firebird:firebird /opt/firebird/UDF/*.*

```

For example, if you UDF name is "AGUDF":

```

gcc -c AGUDF.c
gcc AGUDF.o -o libAGUDF.so -shared
sudo cp ./libAGUDF.so /opt/firebird/UDF/libAGUDF.so
sudo chown firebird:firebird /opt/firebird/UDF/*.*

```

(Note that name of your UDF shared library must have prefix "lib", but when declaring it in database you must specify name without "lib" prefix)

Now your UDF's works!

---

