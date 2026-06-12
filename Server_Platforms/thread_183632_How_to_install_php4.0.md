---
title: "How to install php4.0"
date: 2006-05-28
forum: Server Platforms
---

### Post by eule on 2006-05-28
Hi all!
How can I install php4.0 on ubuntu?
I need this old version of php4, because some php-files use the $DOCUMENT_ROOT variable which is $server[DOCUMENT_ROOT] in newer versions of php...
I tried to compile from source but this gives me the following error: 

```
php-4.0.6# make
Making all in Zend
make[1]: Gehe in Verzeichnis »/home/eule/php-4.0.6/Zend«
/bin/sh ../libtool --silent --mode=compile c++ -DHAVE_CONFIG_H -I. -I. -I../main   -D_REENTRANT -DSUPPORT_UTF8 -DXML_BYTE_ORDER=12 -I../TSRM -DTHREAD=1  -pthread -c zend_language_scanner_cc.cc
In file included from /usr/include/c++/4.0.2/backward/iostream.h:31,
                 from ./FlexLexer.h:47,
                 from zend_language_scanner_cc.cc:240:
/usr/include/c++/4.0.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
zend_language_scanner_cc.cc:2682:25: error: strstream.h: No such file or directory
/usr/include/c++/4.0.2/backward/iostream.h:36: error: 'istream' is already declared in this scope
zend_istdiostream.h:8: error: 'stdiobuf' does not name a type
zend_istdiostream.h:11: error: ISO C++ forbids declaration of 'stdiobuf' with no type
zend_istdiostream.h:11: error: expected ';' before '*' token
zend_istdiostream.h:12: error: expected `;' before '}' token
zend_istdiostream.h: In constructor 'istdiostream::istdiostream(FILE*)':
zend_istdiostream.h:10: error: class 'istdiostream' does not have any field named '_file'
zend_istdiostream.h:10: error: '_file' was not declared in this scope
zend_language_scanner_cc.cc: In function 'void zend_file_handle_dtor(zend_file_handle*)':
zend_language_scanner_cc.cc:2823: error: 'struct std::basic_streambuf<char, std::char_traits<char> >' has no member named 'stdiofile'
zend_language_scanner_cc.cc: In function 'int open_file_for_scanning(zend_file_handle*, zend_compiler_globals*)':
zend_language_scanner_cc.cc:2894: error: invalid conversion from 'int' to 'const char*'
zend_language_scanner_cc.cc:2894: error:   initializing argument 1 of 'std::basic_ifstream<_CharT, _Traits>::basic_ifstream(const char*, std::_Ios_Openmode) [with _CharT = char, _Traits = std::char_traits<char>]'
zend_language_scanner_cc.cc: At global scope:
zend_language_scanner_cc.cc:3038: error: 'istrstream' has not been declared
zend_language_scanner_cc.cc: In function 'int prepare_string_for_scanning(zval*, int**, char*, zend_compiler_globals*)':
zend_language_scanner_cc.cc:3050: error: expected type-specifier before 'istrstream'
zend_language_scanner_cc.cc:3050: error: expected `;' before 'istrstream'
zend_language_scanner_cc.cc:3053: error: no matching function for call to 'ZendFlexLexer::switch_streams(int*&, std::ostream*)'
./FlexLexer.h:117: note: candidates are: virtual void zendFlexLexer::switch_streams(std::istream*, std::ostream*)
zend_language_scanner_cc.cc: In function 'zend_op_array* compile_string(zval*, char*, zend_compiler_globals*)':
zend_language_scanner_cc.cc:3071: error: 'istrstream' was not declared in this scope
zend_language_scanner_cc.cc:3071: error: 'input_stream' was not declared in this scope
zend_language_scanner_cc.cc:3117: error: type '<type error>' argument given to 'delete', expected pointer
zend_language_scanner_cc.cc: In function 'int highlight_string(zval*, zend_syntax_highlighter_ini*, char*)':
zend_language_scanner_cc.cc:3152: error: 'istrstream' was not declared in this scope
zend_language_scanner_cc.cc:3152: error: 'input_stream' was not declared in this scope
zend_language_scanner_cc.cc:3169: error: type '<type error>' argument given to 'delete', expected pointer
zend_language_scanner_cc.cc: In member function 'int ZendFlexLexer::lex_scan(zval*, zend_compiler_globals*)':
zend_language_scanner_cc.cc:4705: error: cannot convert 'std::istream*' to 'istream*' in assignment
zend_language_scanner_cc.cc: In member function 'void zendFlexLexer::yy_load_buffer_state()':
zend_language_scanner_cc.cc:5241: error: cannot convert 'istream*' to 'std::istream*' in assignment
zend_language_scanner_cc.cc: In member function 'void zendFlexLexer::yy_init_buffer(yy_buffer_state*, std::istream*)':
zend_language_scanner_cc.cc:5292: error: cannot convert 'std::istream*' to 'istream*' in assignment
make[1]: *** [zend_language_scanner_cc.lo] Fehler 1
make[1]: Verlasse Verzeichnis »/home/eule/php-4.0.6/Zend«
make: *** [all-recursive] Fehler 1

```

Thx for your help
eule

---

### Post by mrcowcow on 2006-05-28
apt-get install php4

That gets you php4 with apache support.

---

