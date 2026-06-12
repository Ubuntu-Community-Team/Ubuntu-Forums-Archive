---
title: "ivysync installation problem"
date: 2008-08-28
forum: Ubuntu Studio
---

### Post by ToulCit on 2008-08-28
hi hackers,

i was trying to install Ivysync of dyne.org.

i tried to do a ./configure, but it said there was no such file,
so i did a "make" an gave me whole bunch of more errors.

when i tried to do a autoreconf -i --force , it said it needed a configure file.

Can someone help me on this?
I feel stupid even posting it, but i don't know anything about compile i just follow instructions. :S

It also gives some sort of weird error about me not having gtk-2.0 installed, while it is installed by default by ubuntu.

thanks in advance

, Jeroen

p.s. here's my output:

root@toulcit-laptop:/home/toulcit# cd '/home/toulcit/Desktop/ivysync-0.4' 
root@toulcit-laptop:/home/toulcit/Desktop/ivysync-0.4# ./configure
bash: ./configure: No such file or directory
root@toulcit-laptop:/home/toulcit/Desktop/ivysync-0.4# autoreconf -i --force
autoreconf: `configure.ac' or `configure.in' is required
root@toulcit-laptop:/home/toulcit/Desktop/ivysync-0.4# make
cd xmlrpc++ && make
make[1]: Entering directory `/home/toulcit/Desktop/ivysync-0.4/xmlrpc++'
g++ -Wall -ggdb   -c -o XmlRpcClient.o XmlRpcClient.cpp
In file included from XmlRpcClient.h:17,
                 from XmlRpcClient.cpp:2:
XmlRpcSource.h:12:28: error: openssl/crypto.h: No such file or directory
XmlRpcSource.h:13:26: error: openssl/x509.h: No such file or directory
XmlRpcSource.h:14:25: error: openssl/pem.h: No such file or directory
XmlRpcSource.h:15:25: error: openssl/ssl.h: No such file or directory
XmlRpcSource.h:16:25: error: openssl/err.h: No such file or directory
In file included from XmlRpcClient.h:17,
                 from XmlRpcClient.cpp:2:
XmlRpcSource.h:49: error: ISO C++ forbids declaration of ‘SSL_CTX’ with no type
XmlRpcSource.h:49: error: expected ‘;’ before ‘*’ token
XmlRpcSource.h:50: error: ISO C++ forbids declaration of ‘SSL’ with no type
XmlRpcSource.h:50: error: expected ‘;’ before ‘*’ token
XmlRpcSource.h:51: error: ISO C++ forbids declaration of ‘SSL_METHOD’ with no type
XmlRpcSource.h:51: error: expected ‘;’ before ‘*’ token
In file included from XmlRpcClient.cpp:4:
XmlRpcSocket.h:34: error: ‘SSL’ has not been declared
XmlRpcSocket.h:37: error: ‘SSL’ has not been declared
XmlRpcClient.cpp: In constructor ‘XmlRpc::XmlRpcClient::XmlRpcClient(const char*, int, const char*)’:
XmlRpcClient.cpp:44: error: ‘_ssl_ssl’ was not declared in this scope
XmlRpcClient.cpp:44: error: ‘SSL’ was not declared in this scope
XmlRpcClient.cpp:44: error: expected primary-expression before ‘)’ token
XmlRpcClient.cpp:44: error: expected `;' before ‘__null’
XmlRpcClient.cpp: In constructor ‘XmlRpc::XmlRpcClient::XmlRpcClient(const char*, int, const char*, bool)’:
XmlRpcClient.cpp:63: error: ‘_ssl_ssl’ was not declared in this scope
XmlRpcClient.cpp:63: error: ‘SSL’ was not declared in this scope
XmlRpcClient.cpp:63: error: expected primary-expression before ‘)’ token
XmlRpcClient.cpp:63: error: expected `;' before ‘__null’
XmlRpcClient.cpp: In constructor ‘XmlRpc::XmlRpcClient::XmlRpcClient(const char*, int, const char*, const char*, const char*, bool)’:
XmlRpcClient.cpp:113: error: ‘_ssl_ssl’ was not declared in this scope
XmlRpcClient.cpp:113: error: ‘SSL’ was not declared in this scope
XmlRpcClient.cpp:113: error: expected primary-expression before ‘)’ token
XmlRpcClient.cpp:113: error: expected `;' before ‘__null’
XmlRpcClient.cpp: In member function ‘virtual void XmlRpc::XmlRpcClient::close()’:
XmlRpcClient.cpp:138: error: ‘_ssl_ssl’ was not declared in this scope
XmlRpcClient.cpp:138: error: ‘SSL_shutdown’ was not declared in this scope
XmlRpcClient.cpp:145: error: ‘_ssl_ssl’ was not declared in this scope
XmlRpcClient.cpp:145: error: ‘SSL_free’ was not declared in this scope
XmlRpcClient.cpp:147: error: ‘_ssl_ctx’ was not declared in this scope
XmlRpcClient.cpp:147: error: ‘SSL_CTX_free’ was not declared in this scope
XmlRpcClient.cpp: In member function ‘virtual bool XmlRpc::XmlRpcClient::doConnect()’:
XmlRpcClient.cpp:290: error: ‘SSLeay_add_ssl_algorithms’ was not declared in this scope
XmlRpcClient.cpp:291: error: ‘_ssl_meth’ was not declared in this scope
XmlRpcClient.cpp:291: error: ‘SSLv23_client_method’ was not declared in this scope
XmlRpcClient.cpp:292: error: ‘SSL_load_error_strings’ was not declared in this scope
XmlRpcClient.cpp:293: error: ‘_ssl_ctx’ was not declared in this scope
XmlRpcClient.cpp:293: error: ‘SSL_CTX_new’ was not declared in this scope
XmlRpcClient.cpp:294: error: ‘_ssl_ssl’ was not declared in this scope
XmlRpcClient.cpp:294: error: ‘SSL_new’ was not declared in this scope
XmlRpcClient.cpp:295: error: ‘SSL_set_fd’ was not declared in this scope
XmlRpcClient.cpp:296: error: ‘SSL_connect’ was not declared in this scope
XmlRpcClient.cpp:296: warning: unused variable ‘err’
XmlRpcClient.cpp: In member function ‘virtual std::string XmlRpc::XmlRpcClient::generateHeader(const std::string&)’:
XmlRpcClient.cpp:386: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘size_t’
XmlRpcClient.cpp: In member function ‘virtual bool XmlRpc::XmlRpcClient::writeRequest()’:
XmlRpcClient.cpp:398: error: ‘_ssl_ssl’ was not declared in this scope
XmlRpcClient.cpp: In member function ‘virtual bool XmlRpc::XmlRpcClient::readHeader()’:
XmlRpcClient.cpp:420: error: ‘_ssl_ssl’ was not declared in this scope
XmlRpcClient.cpp: In member function ‘virtual bool XmlRpc::XmlRpcClient::readResponse()’:
XmlRpcClient.cpp:492: error: ‘_ssl_ssl’ was not declared in this scope
make[1]: *** [XmlRpcClient.o] Error 1
make[1]: Leaving directory `/home/toulcit/Desktop/ivysync-0.4/xmlrpc++'
make: *** [xmlrpc] Error 2
root@toulcit-laptop:/home/toulcit/Desktop/ivysync-0.4# make install
g++  -I. -Ixmlrpc++ -Wall -O2 -fomit-frame-pointer -ffast-math `pkg-config --cflags gtk+-2.0`  -c -o decoder.o decoder.cpp
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
In file included from decoder.cpp:32:
./gui.h:10:21: error: gtk/gtk.h: No such file or directory
In file included from ./decoder.h:39,
                 from decoder.cpp:30:
./linklist.h:63: error: extra qualification ‘Linklist::’ on member ‘selected’
In file included from decoder.cpp:32:
./gui.h:25: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:25: error: expected ‘;’ before ‘*’ token
./gui.h:31: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:31: error: expected ‘;’ before ‘*’ token
./gui.h:33: error: ISO C++ forbids declaration of ‘GList’ with no type
./gui.h:33: error: expected ‘;’ before ‘*’ token
./gui.h:55: error: ISO C++ forbids declaration of ‘GtkTreeStore’ with no type
./gui.h:55: error: expected ‘;’ before ‘*’ token
./gui.h:57: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:57: error: expected ‘;’ before ‘*’ token
./gui.h:58: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:58: error: expected ‘;’ before ‘*’ token
./gui.h:59: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:59: error: expected ‘;’ before ‘*’ token
./gui.h:60: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:60: error: expected ‘;’ before ‘*’ token
./gui.h:61: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:61: error: expected ‘;’ before ‘*’ token
./gui.h:62: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:62: error: expected ‘;’ before ‘*’ token
./gui.h:63: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:63: error: expected ‘;’ before ‘*’ token
./gui.h:64: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:64: error: expected ‘;’ before ‘*’ token
./gui.h:65: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:65: error: expected ‘;’ before ‘*’ token
./gui.h:66: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:66: error: expected ‘;’ before ‘*’ token
./gui.h:67: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:67: error: expected ‘;’ before ‘*’ token
./gui.h:68: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:68: error: expected ‘;’ before ‘*’ token
./gui.h:69: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:69: error: expected ‘;’ before ‘*’ token
./gui.h:70: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:70: error: expected ‘;’ before ‘*’ token
./gui.h:71: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:71: error: expected ‘;’ before ‘*’ token
./gui.h:72: error: ‘GtkTargetEntry’ does not name a type
./gui.h:89: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:89: error: expected ‘;’ before ‘*’ token
./gui.h:90: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:90: error: expected ‘;’ before ‘*’ token
./gui.h:91: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:91: error: expected ‘;’ before ‘*’ token
./gui.h:92: error: ISO C++ forbids declaration of ‘GtkWidget’ with no type
./gui.h:92: error: expected ‘;’ before ‘*’ token
decoder.cpp: In member function ‘bool Decoder::init(char*)’:
decoder.cpp:67: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:73: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp: In member function ‘bool Decoder::setup(bool*, int)’:
decoder.cpp:100: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp: In member function ‘void Decoder::close()’:
decoder.cpp:117: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp: In member function ‘void Decoder::update()’:
decoder.cpp:178: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:180: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:185: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp: In member function ‘virtual void Decoder::run()’:
decoder.cpp:203: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:209: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:233: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:255: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:263: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:272: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:288: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:290: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:306: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:345: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:359: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:361: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp: In member function ‘void Decoder::flush()’:
decoder.cpp:373: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:380: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp: In member function ‘bool Decoder::clear()’:
decoder.cpp:418: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp: In member function ‘int Decoder::getpos()’:
decoder.cpp:436: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp: In member function ‘void Decoder::setpos(int)’:
decoder.cpp:449: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp: In member function ‘int Decoder::load()’:
decoder.cpp:558: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:572: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:586: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:607: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:616: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:621: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:629: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:633: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:640: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp: In member function ‘int Decoder::save()’:
decoder.cpp:662: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:670: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:674: warning: deprecated conversion from string constant to ‘char*’
decoder.cpp:681: warning: deprecated conversion from string constant to ‘char*’
make: *** [decoder.o] Error 1
root@toulcit-laptop:/home/toulcit/Desktop/ivysync-0.4#

---

