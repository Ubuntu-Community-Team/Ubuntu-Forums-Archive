---
title: "Perl Module Net::Z3950"
date: 2005-11-14
forum: Server Platforms
---

### Post by MatthewMetzger on 2005-11-14
Hello,

I have successfully installed Koha, a library automation system, on Ubuntu breezy. Everything works great except I can't get one very important perl module to install. I run the command

#sudo perl -MCPAN -e 'install "Net::Z3950"'

and everything seems to run fine, until this point.

<terminal output>
Running Mkbootstrap for Net::Z3950 ()
chmod 644 Z3950.bs
rm -f blib/arch/auto/Net/Z3950/Z3950.so
LD_RUN_PATH="" cc  -shared -L/usr/local/lib Z3950.o  -o blib/arch/auto/Net/Z3950/Z3950.so yazwrap/libyazwrap.a  -lyaz -L/usr/lib -lxml2 -lz -lpthread -lm -lssl -lcrypto -lwrap -lnsl
/usr/bin/ld: cannot find -lwrap
collect2: ld returned 1 exit status
make: *** [blib/arch/auto/Net/Z3950/Z3950.so] Error 1
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
</terminal output>

any help in getting this perl module installed would be greatly appreciated. I have installed the yaz packages.

---

### Post by MatthewMetzger on 2005-11-17
Here's the solution that I found with help from the Net::Z3950 mailing list. I believe in posting the solutions I find to problems I ask about on forums.

I installed the package libwrap0-dev via apt-get and the install for Net::Z3950 went perfectly on my Ubuntu 5.10 server.

---

