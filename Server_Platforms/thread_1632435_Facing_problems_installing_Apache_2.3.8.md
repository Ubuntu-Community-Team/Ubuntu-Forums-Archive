---
title: "Facing problems installing Apache 2.3.8"
date: 2010-11-28
forum: Server Platforms
---

### Post by sanchitideas on 2010-11-28
Hi!

I'm a n00b to linux & I'm facing a problem installing Apache 2.3.8 on Ubuntu 10.10.

I followed the instructions given on [http://httpd.apache.org/docs/2.2/install.html](http://httpd.apache.org/docs/2.2/install.html). -

```
# Build and install apr 1.2
cd srclib/apr
./configure --prefix=/usr/local/apr-httpd/
make
make install

# Build and install apr-util 1.2
cd ../apr-util
./configure --prefix=/usr/local/apr-util-httpd/ --with-apr=/usr/local/apr-httpd/
make
make install

# Configure httpd
cd ../../
./configure --with-apr=/usr/local/apr-httpd/ --with-apr-util=/usr/local/apr-util-httpd/ 
```However, I'm getting the following error when I try to configure apr-util -

```
configuring package in xml/expat now
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
/home/sanchit/Documents/httpd-2.3.8/srclib/apr-util/xml/expat/configure: line 2417: syntax error near unexpected token `lt_decl_varnames,'
/home/sanchit/Documents/httpd-2.3.8/srclib/apr-util/xml/expat/configure: line 2417: `lt_if_append_uniq(lt_decl_varnames, SHELL, , ,'
configure failed for xml/expat
```While installing Apache using the bundled apr, i.e. using ```
./configure --with-included-apr
```, I get the following error -

```
configuring package in xml/expat now
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
/home/sanchit/Documents/httpd-2.3.8/srclib/apr-util/xml/expat/configure: line 2417: syntax error near unexpected token `lt_decl_varnames,'
/home/sanchit/Documents/httpd-2.3.8/srclib/apr-util/xml/expat/configure: line 2417: `lt_if_append_uniq(lt_decl_varnames, SHELL, , ,'
configure failed for xml/expat
configure failed for srclib/apr-util
```The line(2417) mentioned in the error is -

```
lt_if_append_uniq(lt_decl_varnames, SHELL, , ,
    lt_dict_add_subkey([lt_decl_dict], [SHELL], [libtool_name],
    [m4_ifval([], [], [SHELL])])
    lt_dict_add_subkey([lt_decl_dict], [SHELL], [value], [1])
    m4_ifval([Shell to use when invoking shell scripts],
    [lt_dict_add_subkey([lt_decl_dict], [SHELL], [description], [Shell to use when invoking shell scripts])])
    lt_dict_add_subkey([lt_decl_dict], [SHELL],
    [tagged?], [m4_ifval([], [yes], [no])]))
```Please tell me how to fix this. Thanks in advance!!!!

Please solve 'The Apache installation conundrum'.

---

### Post by sanchitideas on 2010-11-28
Installed it!

Here's how -

```
apt-get install libexpat1-dev
apt-get install libapr1-dev
 apt-get update
 apt-get install libpcre3 libpcre3-dev
```

Then I downloaded the latest versions of apr & apr-util & replaced them with the contents of folders by the same name in srclib.

Then I did - 

```
./configure --with-included-apr

``` to install Apache

Then I was successful!

---

### Post by James78 on 2010-11-28
2.3.8 is still in Alpha stage. I wouldn't recommend it to anyone for production/ordinary use.

---

