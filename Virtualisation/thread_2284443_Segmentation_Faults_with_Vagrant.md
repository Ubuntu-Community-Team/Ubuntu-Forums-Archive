---
title: "Segmentation Faults with Vagrant"
date: 2015-06-29
forum: Virtualisation
---

### Post by peryton6 on 2015-06-29
Hello everyone,

I'm trying to set up a Vagrant box on Ubuntu 14.10 and I'm having trouble getting over this error. I first installed VirtualBox and then installed Vagrant with aptitude.

Now when I try to run 'vagrant init' or 'vagrant up' I get the following error:

```
vagrant box add precise32 http://files.vagrantup.com/precise32.box
/usr/lib/ruby/2.1.0/rubygems/core_ext/kernel_require.rb:55: [BUG] Segmentation fault at 0x00000000000000
ruby 2.1.2p95 (2014-05-08) [x86_64-linux-gnu]

-- Control frame information -----------------------------------------------
c:0010 p:---- s:0063 e:000062 CFUNC  :require
c:0009 p:0115 s:0059 e:000058 METHOD /usr/lib/ruby/2.1.0/rubygems/core_ext/kernel_require.rb:55
c:0008 p:0031 s:0049 e:000048 TOP    /usr/lib/ruby/2.1.0/openssl.rb:21 [FINISH]
c:0007 p:---- s:0047 e:000046 CFUNC  :require
c:0006 p:0115 s:0043 e:000042 METHOD /usr/lib/ruby/2.1.0/rubygems/core_ext/kernel_require.rb:55
c:0005 p:0294 s:0033 e:000032 TOP    /usr/lib/ruby/vendor_ruby/vagrant.rb:55 [FINISH]
c:0004 p:---- s:0027 e:000026 CFUNC  :require
c:0003 p:0115 s:0023 e:000022 METHOD /usr/lib/ruby/2.1.0/rubygems/core_ext/kernel_require.rb:55
c:0002 p:0128 s:0013 E:001720 EVAL   /usr/bin/vagrant:24 [FINISH]
c:0001 p:0000 s:0002 E:001ac8 TOP    [FINISH]

-- Ruby level backtrace information ----------------------------------------
/usr/bin/vagrant:24:in `<main>'
/usr/lib/ruby/2.1.0/rubygems/core_ext/kernel_require.rb:55:in `require'
/usr/lib/ruby/2.1.0/rubygems/core_ext/kernel_require.rb:55:in `require'
/usr/lib/ruby/vendor_ruby/vagrant.rb:55:in `<top (required)>'
/usr/lib/ruby/2.1.0/rubygems/core_ext/kernel_require.rb:55:in `require'
/usr/lib/ruby/2.1.0/rubygems/core_ext/kernel_require.rb:55:in `require'
/usr/lib/ruby/2.1.0/openssl.rb:21:in `<top (required)>'
/usr/lib/ruby/2.1.0/rubygems/core_ext/kernel_require.rb:55:in `require'
/usr/lib/ruby/2.1.0/rubygems/core_ext/kernel_require.rb:55:in `require'

-- C level backtrace information -------------------------------------------
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x18a017) [0x7f6c8cb3b017]
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x18a0e3) [0x7f6c8cb3b0e3]
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x6dac3) [0x7f6c8ca1eac3] iofclose.c:57
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(rb_bug+0xb3) [0x7f6c8ca1f133] iofgetpos.c:50
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x12068e) [0x7f6c8cad168e] rpc_cmsg.c:193
/lib/x86_64-linux-gnu/libc.so.6(+0x36eb0) [0x7f6c8c623eb0] ../sysdeps/posix/killpg.c:37
/lib/x86_64-linux-gnu/libc.so.6(malloc_usable_size+0x26) [0x7f6c8c6704f6] malloc.c:4567
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x8b102) [0x7f6c8ca3c102] ../string/str-two-way.h:456
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(rb_str_free+0x46) [0x7f6c8cae3336] ../sysdeps/unix/getlogin.c:64
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x89b53) [0x7f6c8ca3ab53] ../sysdeps/x86_64/multiarch/../strcmp.S:1268
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x8a9ad) [0x7f6c8ca3b9ad] ../sysdeps/x86_64/strrchr.S:188
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(rb_node_newnode+0x2b) [0x7f6c8ca3bb7b] strsignal.c:95
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0xc7232) [0x7f6c8ca78232] fnmatch_loop.c:542
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0xd7128) [0x7f6c8ca88128] regex_internal.c:989
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0xe0c92) [0x7f6c8ca91c92] ../sysdeps/posix/getaddrinfo.c:948
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x18d8ea) [0x7f6c8cb3e8ea]
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(rb_parser_compile_file_path+0x78) [0x7f6c8ca7cd78] regcomp.c:331
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x11eae0) [0x7f6c8cacfae0] bindrsvprt.c:106
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(rb_ensure+0x111) [0x7f6c8ca24321] wgenops.c:113
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(rb_load_file_str+0x59) [0x7f6c8cacf8b9] bindrsvprt.c:67
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x753db) [0x7f6c8ca263db] wfileops.c:963
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(rb_require_safe+0x694) [0x7f6c8ca27c64] libioP.h:888
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x1742d6) [0x7f6c8cb252d6]
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x1791e3) [0x7f6c8cb2a1e3]
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x17eca8) [0x7f6c8cb2fca8]
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(rb_iseq_eval+0x129) [0x7f6c8cb326d9]
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x75430) [0x7f6c8ca26430] wfileops.c:964
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(rb_require_safe+0x694) [0x7f6c8ca27c64] libioP.h:888
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x1742d6) [0x7f6c8cb252d6]
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x1791e3) [0x7f6c8cb2a1e3]
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x17eca8) [0x7f6c8cb2fca8]
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(rb_iseq_eval+0x129) [0x7f6c8cb326d9]
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x75430) [0x7f6c8ca26430] wfileops.c:964
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(rb_require_safe+0x694) [0x7f6c8ca27c64] libioP.h:888
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x1742d6) [0x7f6c8cb252d6]
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x1791e3) [0x7f6c8cb2a1e3]
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x17eca8) [0x7f6c8cb2fca8]
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(rb_iseq_eval_main+0x7f) [0x7f6c8cb3278f]
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(+0x7116b) [0x7f6c8ca2216b] libioP.h:889
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(ruby_exec_node+0x1d) [0x7f6c8ca23a5d] wgenops.c:469
/usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1(ruby_run_node+0x1e) [0x7f6c8ca2531e] wfileops.c:154
/usr/bin/ruby() [0x40086b]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf5) [0x7f6c8c60eec5] libc-start.c:287
/usr/bin/ruby() [0x400899]

-- Other runtime information -----------------------------------------------

* Loaded script: /usr/bin/vagrant

* Loaded features:

    0 enumerator.so
    1 /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/encdb.so
    2 /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/trans/transdb.so
    3 /usr/lib/x86_64-linux-gnu/ruby/2.1.0/rbconfig.rb
    4 /usr/lib/ruby/2.1.0/rubygems/compatibility.rb
    5 /usr/lib/ruby/2.1.0/rubygems/defaults.rb
    6 /usr/lib/ruby/2.1.0/rubygems/deprecate.rb
    7 /usr/lib/ruby/2.1.0/rubygems/errors.rb
    8 /usr/lib/ruby/2.1.0/rubygems/version.rb
    9 /usr/lib/ruby/2.1.0/rubygems/requirement.rb
   10 /usr/lib/ruby/2.1.0/rubygems/platform.rb
   11 /usr/lib/ruby/2.1.0/rubygems/basic_specification.rb
   12 /usr/lib/ruby/2.1.0/rubygems/stub_specification.rb
   13 /usr/lib/ruby/2.1.0/rubygems/util/stringio.rb
   14 /usr/lib/ruby/2.1.0/rubygems/specification.rb
   15 /usr/lib/ruby/2.1.0/rubygems/exceptions.rb
   16 /usr/lib/ruby/vendor_ruby/rubygems/defaults/operating_system.rb
   17 /usr/lib/ruby/2.1.0/rubygems/core_ext/kernel_gem.rb
   18 thread.rb
   19 /usr/lib/x86_64-linux-gnu/ruby/2.1.0/thread.so
   20 /usr/lib/ruby/2.1.0/monitor.rb
   21 /usr/lib/ruby/2.1.0/rubygems/core_ext/kernel_require.rb
   22 /usr/lib/ruby/2.1.0/rubygems.rb
   23 /usr/lib/ruby/vendor_ruby/log4r/version.rb
   24 /usr/lib/ruby/vendor_ruby/log4r/config.rb
   25 /usr/lib/ruby/vendor_ruby/log4r/base.rb
   26 /usr/lib/ruby/2.1.0/singleton.rb
   27 /usr/lib/ruby/vendor_ruby/log4r/repository.rb
   28 /usr/lib/ruby/vendor_ruby/log4r/logevent.rb
   29 /usr/lib/ruby/vendor_ruby/log4r/loggerfactory.rb
   30 /usr/lib/ruby/vendor_ruby/log4r/staticlogger.rb
   31 /usr/lib/ruby/vendor_ruby/log4r/logger.rb
   32 /usr/lib/ruby/vendor_ruby/log4r/outputter/outputterfactory.rb
   33 /usr/lib/ruby/vendor_ruby/log4r/formatter/formatter.rb
   34 /usr/lib/ruby/vendor_ruby/log4r/outputter/outputter.rb
   35 /usr/lib/ruby/vendor_ruby/log4r/outputter/iooutputter.rb
   36 /usr/lib/ruby/vendor_ruby/log4r/outputter/fileoutputter.rb
   37 /usr/lib/ruby/vendor_ruby/log4r/outputter/consoleoutputters.rb
   38 /usr/lib/ruby/vendor_ruby/log4r/outputter/staticoutputter.rb
   39 /usr/lib/x86_64-linux-gnu/ruby/2.1.0/etc.so
   40 /usr/lib/ruby/2.1.0/fileutils.rb
   41 /usr/lib/ruby/vendor_ruby/log4r/outputter/rollingfileoutputter.rb
   42 /usr/lib/ruby/vendor_ruby/log4r/GDC.rb
   43 /usr/lib/ruby/vendor_ruby/log4r/MDC.rb
   44 /usr/lib/ruby/vendor_ruby/log4r/NDC.rb
   45 /usr/lib/ruby/vendor_ruby/log4r/formatter/patternformatter.rb
   46 /usr/lib/ruby/vendor_ruby/log4r.rb
   47 /usr/lib/ruby/2.1.0/rubygems/dependency.rb
   48 /usr/lib/ruby/2.1.0/rubygems/path_support.rb
   49 /home/drunix/.rvm/gems/ruby-2.2.1/gems/json-1.8.2/lib/json/version.rb
   50 /usr/lib/ruby/2.1.0/ostruct.rb
   51 /home/drunix/.rvm/gems/ruby-2.2.1/gems/json-1.8.2/lib/json/generic_object.rb
   52 /home/drunix/.rvm/gems/ruby-2.2.1/gems/json-1.8.2/lib/json/common.rb
   53 /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_16be.so
   54 /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_16le.so
   55 /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_32be.so
   56 /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_32le.so
   57 /home/drunix/.rvm/gems/ruby-2.2.1/gems/json-1.8.2/lib/json/ext/parser.so
   58 /home/drunix/.rvm/gems/ruby-2.2.1/gems/json-1.8.2/lib/json/ext/generator.so
   59 /home/drunix/.rvm/gems/ruby-2.2.1/gems/json-1.8.2/lib/json/ext.rb
   60 /home/drunix/.rvm/gems/ruby-2.2.1/gems/json-1.8.2/lib/json.rb
   61 /usr/lib/x86_64-linux-gnu/ruby/2.1.0/pathname.so
   62 /usr/lib/ruby/2.1.0/pathname.rb
   63 /usr/lib/x86_64-linux-gnu/ruby/2.1.0/stringio.so
   64 /usr/lib/ruby/vendor_ruby/childprocess/errors.rb
   65 /usr/lib/ruby/vendor_ruby/childprocess/abstract_process.rb
   66 /usr/lib/ruby/vendor_ruby/childprocess/abstract_io.rb
   67 /usr/lib/x86_64-linux-gnu/ruby/2.1.0/fcntl.so
   68 /usr/lib/ruby/vendor_ruby/childprocess/unix/io.rb
   69 /usr/lib/ruby/vendor_ruby/childprocess/unix/process.rb
   70 /usr/lib/ruby/vendor_ruby/childprocess/unix/fork_exec_process.rb
   71 /usr/lib/ruby/vendor_ruby/childprocess/unix.rb
   72 /usr/lib/ruby/vendor_ruby/childprocess.rb
   73 /usr/lib/ruby/vendor_ruby/i18n/version.rb
   74 /usr/lib/ruby/2.1.0/cgi/core.rb
   75 /usr/lib/ruby/2.1.0/cgi/util.rb
   76 /usr/lib/ruby/2.1.0/cgi/cookie.rb
   77 /usr/lib/ruby/2.1.0/cgi.rb
   78 /usr/lib/ruby/vendor_ruby/i18n/exceptions.rb
   79 /usr/lib/ruby/vendor_ruby/i18n/interpolate/ruby.rb
   80 /usr/lib/ruby/vendor_ruby/i18n.rb
   81 /usr/lib/x86_64-linux-gnu/ruby/2.1.0/digest.so
   82 /usr/lib/ruby/2.1.0/digest.rb
   83 /usr/lib/x86_64-linux-gnu/ruby/2.1.0/openssl.so
   84 /usr/lib/ruby/2.1.0/openssl/bn.rb
   85 /usr/lib/ruby/2.1.0/openssl/cipher.rb

* Process memory map:

00400000-00401000 r-xp 00000000 08:17 4596234                            /usr/bin/ruby2.1
00600000-00601000 r--p 00000000 08:17 4596234                            /usr/bin/ruby2.1
00601000-00602000 rw-p 00001000 08:17 4596234                            /usr/bin/ruby2.1
01ee8000-026b3000 rw-p 00000000 00:00 0                                  [heap]
7f6c88763000-7f6c88779000 r-xp 00000000 08:17 1577795                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f6c88779000-7f6c88978000 ---p 00016000 08:17 1577795                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f6c88978000-7f6c88979000 r--p 00015000 08:17 1577795                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f6c88979000-7f6c8897a000 rw-p 00016000 08:17 1577795                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f6c8897a000-7f6c8897d000 r-xp 00000000 08:17 4595212                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/digest.so
7f6c8897d000-7f6c88b7c000 ---p 00003000 08:17 4595212                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/digest.so
7f6c88b7c000-7f6c88b7d000 r--p 00002000 08:17 4595212                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/digest.so
7f6c88b7d000-7f6c88b7e000 rw-p 00003000 08:17 4595212                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/digest.so
7f6c88b7e000-7f6c88d35000 r-xp 00000000 08:17 1581156                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
7f6c88d35000-7f6c88f34000 ---p 001b7000 08:17 1581156                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
7f6c88f34000-7f6c88f51000 r--p 001b6000 08:17 1581156                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
7f6c88f51000-7f6c88f5d000 rw-p 001d3000 08:17 1581156                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
7f6c88f5d000-7f6c88f61000 rw-p 00000000 00:00 0 
7f6c88f61000-7f6c88fb7000 r-xp 00000000 08:17 1581139                    /lib/x86_64-linux-gnu/libssl.so.1.0.0
7f6c88fb7000-7f6c891b7000 ---p 00056000 08:17 1581139                    /lib/x86_64-linux-gnu/libssl.so.1.0.0
7f6c891b7000-7f6c891bb000 r--p 00056000 08:17 1581139                    /lib/x86_64-linux-gnu/libssl.so.1.0.0
7f6c891bb000-7f6c891c2000 rw-p 0005a000 08:17 1581139                    /lib/x86_64-linux-gnu/libssl.so.1.0.0
7f6c891c2000-7f6c89210000 r-xp 00000000 08:17 4595281                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/openssl.so
7f6c89210000-7f6c89410000 ---p 0004e000 08:17 4595281                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/openssl.so
7f6c89410000-7f6c89411000 r--p 0004e000 08:17 4595281                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/openssl.so
7f6c89411000-7f6c89413000 rw-p 0004f000 08:17 4595281                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/openssl.so
7f6c89413000-7f6c89414000 rw-p 00000000 00:00 0 
7f6c89414000-7f6c89415000 r-xp 00000000 08:17 4595214                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/fcntl.so
7f6c89415000-7f6c89614000 ---p 00001000 08:17 4595214                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/fcntl.so
7f6c89614000-7f6c89615000 r--p 00000000 08:17 4595214                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/fcntl.so
7f6c89615000-7f6c89616000 rw-p 00001000 08:17 4595214                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/fcntl.so
7f6c89616000-7f6c8961d000 r-xp 00000000 08:17 4595283                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/stringio.so
7f6c8961d000-7f6c8981c000 ---p 00007000 08:17 4595283                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/stringio.so
7f6c8981c000-7f6c8981d000 r--p 00006000 08:17 4595283                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/stringio.so
7f6c8981d000-7f6c8981e000 rw-p 00007000 08:17 4595283                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/stringio.so
7f6c8981e000-7f6c89824000 r-xp 00000000 08:17 4595190                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/pathname.so
7f6c89824000-7f6c89a23000 ---p 00006000 08:17 4595190                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/pathname.so
7f6c89a23000-7f6c89a24000 r--p 00005000 08:17 4595190                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/pathname.so
7f6c89a24000-7f6c89a25000 rw-p 00006000 08:17 4595190                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/pathname.so
7f6c89a25000-7f6c89a2f000 r-xp 00000000 08:17 1972459                    /home/drunix/.rvm/gems/ruby-2.2.1/gems/json-1.8.2/lib/json/ext/generator.so
7f6c89a2f000-7f6c89c2e000 ---p 0000a000 08:17 1972459                    /home/drunix/.rvm/gems/ruby-2.2.1/gems/json-1.8.2/lib/json/ext/generator.so
7f6c89c2e000-7f6c89c2f000 r--p 00009000 08:17 1972459                    /home/drunix/.rvm/gems/ruby-2.2.1/gems/json-1.8.2/lib/json/ext/generator.so
7f6c89c2f000-7f6c89c30000 rw-p 0000a000 08:17 1972459                    /home/drunix/.rvm/gems/ruby-2.2.1/gems/json-1.8.2/lib/json/ext/generator.so
7f6c89c30000-7f6c89c31000 r-xp 00000000 08:17 4595274                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_32le.so
7f6c89c31000-7f6c89e30000 ---p 00001000 08:17 4595274                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_32le.so
7f6c89e30000-7f6c89e31000 r--p 00000000 08:17 4595274                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_32le.so
7f6c89e31000-7f6c89e32000 rw-p 00001000 08:17 4595274                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_32le.so
7f6c89e32000-7f6c89e33000 r-xp 00000000 08:17 4595271                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_32be.so
7f6c89e33000-7f6c8a032000 ---p 00001000 08:17 4595271                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_32be.so
7f6c8a032000-7f6c8a033000 r--p 00000000 08:17 4595271                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_32be.so
7f6c8a033000-7f6c8a034000 rw-p 00001000 08:17 4595271                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_32be.so
7f6c8a034000-7f6c8a035000 r-xp 00000000 08:17 4595270                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_16le.so
7f6c8a035000-7f6c8a235000 ---p 00001000 08:17 4595270                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_16le.so
7f6c8a235000-7f6c8a236000 r--p 00001000 08:17 4595270                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_16le.so
7f6c8a236000-7f6c8a237000 rw-p 00002000 08:17 4595270                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_16le.so
7f6c8a237000-7f6c8a238000 r-xp 00000000 08:17 4595225                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_16be.so
7f6c8a238000-7f6c8a438000 ---p 00001000 08:17 4595225                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_16be.so
7f6c8a438000-7f6c8a439000 r--p 00001000 08:17 4595225                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_16be.so
7f6c8a439000-7f6c8a43a000 rw-p 00002000 08:17 4595225                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/utf_16be.so
7f6c8a43a000-7f6c8a6fb000 r-xp 00000000 08:17 1848948                    /home/drunix/.rvm/rubies/ruby-2.2.1/lib/libruby.so.2.2.0
7f6c8a6fb000-7f6c8a8fa000 ---p 002c1000 08:17 1848948                    /home/drunix/.rvm/rubies/ruby-2.2.1/lib/libruby.so.2.2.0
7f6c8a8fa000-7f6c8a900000 r--p 002c0000 08:17 1848948                    /home/drunix/.rvm/rubies/ruby-2.2.1/lib/libruby.so.2.2.0
7f6c8a900000-7f6c8a903000 rw-p 002c6000 08:17 1848948                    /home/drunix/.rvm/rubies/ruby-2.2.1/lib/libruby.so.2.2.0
7f6c8a903000-7f6c8a914000 rw-p 00000000 00:00 0 
7f6c8a914000-7f6c8a91a000 r-xp 00000000 08:17 1972468                    /home/drunix/.rvm/gems/ruby-2.2.1/gems/json-1.8.2/lib/json/ext/parser.so
7f6c8a91a000-7f6c8ab19000 ---p 00006000 08:17 1972468                    /home/drunix/.rvm/gems/ruby-2.2.1/gems/json-1.8.2/lib/json/ext/parser.so
7f6c8ab19000-7f6c8ab1a000 r--p 00005000 08:17 1972468                    /home/drunix/.rvm/gems/ruby-2.2.1/gems/json-1.8.2/lib/json/ext/parser.so
7f6c8ab1a000-7f6c8ab1b000 rw-p 00006000 08:17 1972468                    /home/drunix/.rvm/gems/ruby-2.2.1/gems/json-1.8.2/lib/json/ext/parser.so
7f6c8ab1b000-7f6c8ab1e000 r-xp 00000000 08:17 4595188                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/etc.so
7f6c8ab1e000-7f6c8ad1d000 ---p 00003000 08:17 4595188                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/etc.so
7f6c8ad1d000-7f6c8ad1e000 r--p 00002000 08:17 4595188                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/etc.so
7f6c8ad1e000-7f6c8ad1f000 rw-p 00003000 08:17 4595188                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/etc.so
7f6c8ad1f000-7f6c8ad22000 r-xp 00000000 08:17 4595213                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/thread.so
7f6c8ad22000-7f6c8af21000 ---p 00003000 08:17 4595213                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/thread.so
7f6c8af21000-7f6c8af22000 r--p 00002000 08:17 4595213                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/thread.so
7f6c8af22000-7f6c8af23000 rw-p 00003000 08:17 4595213                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/thread.so
7f6c8af23000-7f6c8af25000 r-xp 00000000 08:17 4595250                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/trans/transdb.so
7f6c8af25000-7f6c8b125000 ---p 00002000 08:17 4595250                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/trans/transdb.so
7f6c8b125000-7f6c8b126000 r--p 00002000 08:17 4595250                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/trans/transdb.so
7f6c8b126000-7f6c8b127000 rw-p 00003000 08:17 4595250                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/trans/transdb.so
7f6c8b127000-7f6c8b129000 r-xp 00000000 08:17 4595238                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/encdb.so
7f6c8b129000-7f6c8b328000 ---p 00002000 08:17 4595238                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/encdb.so
7f6c8b328000-7f6c8b329000 r--p 00001000 08:17 4595238                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/encdb.so
7f6c8b329000-7f6c8b32a000 rw-p 00002000 08:17 4595238                    /usr/lib/x86_64-linux-gnu/ruby/2.1.0/enc/encdb.so
7f6c8b32a000-7f6c8ba0c000 r--p 00000000 08:17 4596703                    /usr/lib/locale/locale-archive
7f6c8ba0c000-7f6c8bb11000 r-xp 00000000 08:17 1579493                    /lib/x86_64-linux-gnu/libm-2.19.so
7f6c8bb11000-7f6c8bd10000 ---p 00105000 08:17 1579493                    /lib/x86_64-linux-gnu/libm-2.19.so
7f6c8bd10000-7f6c8bd11000 r--p 00104000 08:17 1579493                    /lib/x86_64-linux-gnu/libm-2.19.so
7f6c8bd11000-7f6c8bd12000 rw-p 00105000 08:17 1579493                    /lib/x86_64-linux-gnu/libm-2.19.so
7f6c8bd12000-7f6c8bd1b000 r-xp 00000000 08:17 1579504                    /lib/x86_64-linux-gnu/libcrypt-2.19.so
7f6c8bd1b000-7f6c8bf1b000 ---p 00009000 08:17 1579504                    /lib/x86_64-linux-gnu/libcrypt-2.19.so
7f6c8bf1b000-7f6c8bf1c000 r--p 00009000 08:17 1579504                    /lib/x86_64-linux-gnu/libcrypt-2.19.so
7f6c8bf1c000-7f6c8bf1d000 rw-p 0000a000 08:17 1579504                    /lib/x86_64-linux-gnu/libcrypt-2.19.so
7f6c8bf1d000-7f6c8bf4b000 rw-p 00000000 00:00 0 
7f6c8bf4b000-7f6c8bf4e000 r-xp 00000000 08:17 1579500                    /lib/x86_64-linux-gnu/libdl-2.19.so
7f6c8bf4e000-7f6c8c14d000 ---p 00003000 08:17 1579500                    /lib/x86_64-linux-gnu/libdl-2.19.so
7f6c8c14d000-7f6c8c14e000 r--p 00002000 08:17 1579500                    /lib/x86_64-linux-gnu/libdl-2.19.so
7f6c8c14e000-7f6c8c14f000 rw-p 00003000 08:17 1579500                    /lib/x86_64-linux-gnu/libdl-2.19.so
7f6c8c14f000-7f6c8c1cd000 r-xp 00000000 08:17 4599317                    /usr/lib/x86_64-linux-gnu/libgmp.so.10.2.0
7f6c8c1cd000-7f6c8c3cd000 ---p 0007e000 08:17 4599317                    /usr/lib/x86_64-linux-gnu/libgmp.so.10.2.0
7f6c8c3cd000-7f6c8c3ce000 r--p 0007e000 08:17 4599317                    /usr/lib/x86_64-linux-gnu/libgmp.so.10.2.0
7f6c8c3ce000-7f6c8c3cf000 rw-p 0007f000 08:17 4599317                    /usr/lib/x86_64-linux-gnu/libgmp.so.10.2.0
7f6c8c3cf000-7f6c8c3e8000 r-xp 00000000 08:17 1579501                    /lib/x86_64-linux-gnu/libpthread-2.19.so
7f6c8c3e8000-7f6c8c5e7000 ---p 00019000 08:17 1579501                    /lib/x86_64-linux-gnu/libpthread-2.19.so
7f6c8c5e7000-7f6c8c5e8000 r--p 00018000 08:17 1579501                    /lib/x86_64-linux-gnu/libpthread-2.19.so
7f6c8c5e8000-7f6c8c5e9000 rw-p 00019000 08:17 1579501                    /lib/x86_64-linux-gnu/libpthread-2.19.so
7f6c8c5e9000-7f6c8c5ed000 rw-p 00000000 00:00 0 
7f6c8c5ed000-7f6c8c7a7000 r-xp 00000000 08:17 1579512                    /lib/x86_64-linux-gnu/libc-2.19.so
7f6c8c7a7000-7f6c8c9a6000 ---p 001ba000 08:17 1579512                    /lib/x86_64-linux-gnu/libc-2.19.so
7f6c8c9a6000-7f6c8c9aa000 r--p 001b9000 08:17 1579512                    /lib/x86_64-linux-gnu/libc-2.19.so
7f6c8c9aa000-7f6c8c9ac000 rw-p 001bd000 08:17 1579512                    /lib/x86_64-linux-gnu/libc-2.19.so
7f6c8c9ac000-7f6c8c9b1000 rw-p 00000000 00:00 0 
7f6c8c9b1000-7f6c8cbfe000 r-xp 00000000 08:17 4595175                    /usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1.0
7f6c8cbfe000-7f6c8cdfd000 ---p 0024d000 08:17 4595175                    /usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1.0
7f6c8cdfd000-7f6c8ce03000 r--p 0024c000 08:17 4595175                    /usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1.0
7f6c8ce03000-7f6c8ce07000 rw-p 00252000 08:17 4595175                    /usr/lib/x86_64-linux-gnu/libruby-2.1.so.2.1.0
7f6c8ce07000-7f6c8ce2b000 rw-p 00000000 00:00 0 
7f6c8ce2b000-7f6c8ce4e000 r-xp 00000000 08:17 1579507                    /lib/x86_64-linux-gnu/ld-2.19.so
7f6c8cf2f000-7f6c8d035000 rw-p 00000000 00:00 0 
7f6c8d046000-7f6c8d047000 rw-p 00000000 00:00 0 
7f6c8d047000-7f6c8d048000 ---p 00000000 00:00 0 
7f6c8d048000-7f6c8d04d000 rw-p 00000000 00:00 0                          [stack:13127]
7f6c8d04d000-7f6c8d04e000 r--p 00022000 08:17 1579507                    /lib/x86_64-linux-gnu/ld-2.19.so
7f6c8d04e000-7f6c8d04f000 rw-p 00023000 08:17 1579507                    /lib/x86_64-linux-gnu/ld-2.19.so
7f6c8d04f000-7f6c8d050000 rw-p 00000000 00:00 0 
7ffd70a8c000-7ffd70aad000 rw-p 00000000 00:00 0 
7ffd70bec000-7ffd70bee000 r-xp 00000000 00:00 0                          [vdso]
7ffd70bee000-7ffd70bf0000 r--p 00000000 00:00 0                          [vvar]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]


[NOTE]
You may have encountered a bug in the Ruby interpreter or extension libraries.
Bug reports are welcome.
For details: http://www.ruby-lang.org/bugreport.html

Aborted (core dumped)


```

Sorry for the long paste but I'm not really sure where to go from here! Googling around and checking the forums makes it seem like a lot of other people running Vagrant on Ubuntu have had problems with incompatable libraries, I'm not sure if that would give me the segmentation fault nor what the first steps to correcting this might be. Thanks for any input!

---

### Post by v3.xx on 2015-06-29
First observation is 
14.10 reaches EOL in a few weeks.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I do not run vagrant box, but got some hits on the second line.
[https://www.google.com/search?client=ubuntu&channel=fs&q=kernel_require.rb%3A55%3A+](https://www.google.com/search?client=ubuntu&channel=fs&q=kernel_require.rb%3A55%3A+)[BUG]&ie=utf-8&oe=utf-8
Hope it helps, thats all I got, good luck.

---

