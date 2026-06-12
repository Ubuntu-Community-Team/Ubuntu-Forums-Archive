---
title: "Bugzilla 3.4.4 install perl problem"
date: 2009-12-04
forum: Server Platforms
---

### Post by david_vanwoensel on 2009-12-04
Hello,
I'm trying to install a bugzilla 3.4.4 server on ubuntu 8.04 LTS
when I run the checksetup.pl I get a message of one missing required perl module : templates
I've tried installing it through the suggested command (sudo  /usr/bin/perl install-module.pl Template) without success. Anyone knows what's going on?

```
Template-Toolkit-2.22/lib/Template/Stash.pm
Template-Toolkit-2.22/lib/Template/Test.pm
Template-Toolkit-2.22/lib/Template/Toolkit.pod
Template-Toolkit-2.22/lib/Template/Tools/
Template-Toolkit-2.22/lib/Template/Tools/tpage.pod
Template-Toolkit-2.22/lib/Template/Tools/ttree.pod
Template-Toolkit-2.22/lib/Template/Tools.pod
Template-Toolkit-2.22/lib/Template/Tutorial/
Template-Toolkit-2.22/lib/Template/Tutorial/Datafile.pod
Template-Toolkit-2.22/lib/Template/Tutorial/Web.pod
Template-Toolkit-2.22/lib/Template/Tutorial.pod
Template-Toolkit-2.22/lib/Template/View.pm
Template-Toolkit-2.22/lib/Template/VMethods.pm
Template-Toolkit-2.22/lib/Template.pm
Template-Toolkit-2.22/Makefile.PL
Template-Toolkit-2.22/MANIFEST
Template-Toolkit-2.22/META.yml
Template-Toolkit-2.22/parser/
Template-Toolkit-2.22/parser/Grammar.pm.skel
Template-Toolkit-2.22/parser/Parser.yp
Template-Toolkit-2.22/parser/README
Template-Toolkit-2.22/parser/yc
Template-Toolkit-2.22/README
Template-Toolkit-2.22/t/
Template-Toolkit-2.22/t/args.t
Template-Toolkit-2.22/t/assert.t
Template-Toolkit-2.22/t/base.t
Template-Toolkit-2.22/t/binop.t
Template-Toolkit-2.22/t/block.t
Template-Toolkit-2.22/t/blocks.t
Template-Toolkit-2.22/t/capture.t
Template-Toolkit-2.22/t/case.t
Template-Toolkit-2.22/t/cgi.t
Template-Toolkit-2.22/t/chomp.t
Template-Toolkit-2.22/t/compile1.t
Template-Toolkit-2.22/t/compile2.t
Template-Toolkit-2.22/t/compile3.t
Template-Toolkit-2.22/t/compile4.t
Template-Toolkit-2.22/t/compile5.t
Template-Toolkit-2.22/t/config.t
Template-Toolkit-2.22/t/constants.t
Template-Toolkit-2.22/t/context.t
Template-Toolkit-2.22/t/datafile.t
Template-Toolkit-2.22/t/date.t
Template-Toolkit-2.22/t/debug.t
Template-Toolkit-2.22/t/directive.t
Template-Toolkit-2.22/t/directry.t
Template-Toolkit-2.22/t/document.t
Template-Toolkit-2.22/t/dumper.t
Template-Toolkit-2.22/t/error.t
Template-Toolkit-2.22/t/evalperl.t
Template-Toolkit-2.22/t/exception.t
Template-Toolkit-2.22/t/factory.t
Template-Toolkit-2.22/t/file.t
Template-Toolkit-2.22/t/fileline.t
Template-Toolkit-2.22/t/filter.t
Template-Toolkit-2.22/t/foreach.t
Template-Toolkit-2.22/t/format.t
Template-Toolkit-2.22/t/html.t
Template-Toolkit-2.22/t/image.t
Template-Toolkit-2.22/t/include.t
Template-Toolkit-2.22/t/iterator.t
Template-Toolkit-2.22/t/leak.t
Template-Toolkit-2.22/t/lib/
Template-Toolkit-2.22/t/lib/Template/
Template-Toolkit-2.22/t/lib/Template/Plugin/
Template-Toolkit-2.22/t/lib/Template/Plugin/ProcBar.pm
Template-Toolkit-2.22/t/lib/Template/Plugin/ProcFoo.pm
Template-Toolkit-2.22/t/lib/Template/Plugin/Simple.pm
Template-Toolkit-2.22/t/list.t
Template-Toolkit-2.22/t/macro.t
Template-Toolkit-2.22/t/math.t
Template-Toolkit-2.22/t/object.t
Template-Toolkit-2.22/t/output.t
Template-Toolkit-2.22/t/parser.t
Template-Toolkit-2.22/t/plugins.t
Template-Toolkit-2.22/t/plusfile.t
Template-Toolkit-2.22/t/pod.t
Template-Toolkit-2.22/t/prefix.t
Template-Toolkit-2.22/t/proc.t
Template-Toolkit-2.22/t/process.t
Template-Toolkit-2.22/t/provider.t
Template-Toolkit-2.22/t/README
Template-Toolkit-2.22/t/ref.t
Template-Toolkit-2.22/t/scalar.t
Template-Toolkit-2.22/t/service.t
Template-Toolkit-2.22/t/skel.t
Template-Toolkit-2.22/t/stash-xs-unicode.t
Template-Toolkit-2.22/t/stash-xs.t
Template-Toolkit-2.22/t/stash.t
Template-Toolkit-2.22/t/stashc.t
Template-Toolkit-2.22/t/stop.t
Template-Toolkit-2.22/t/strcat.t
Template-Toolkit-2.22/t/strict.t
Template-Toolkit-2.22/t/string.t
Template-Toolkit-2.22/t/switch.t
Template-Toolkit-2.22/t/table.t
Template-Toolkit-2.22/t/tags.t
Template-Toolkit-2.22/t/template.t
Template-Toolkit-2.22/t/test/
Template-Toolkit-2.22/t/test/dir/
Template-Toolkit-2.22/t/test/dir/file1
Template-Toolkit-2.22/t/test/dir/file2
Template-Toolkit-2.22/t/test/dir/sub_one/
Template-Toolkit-2.22/t/test/dir/sub_one/bar
Template-Toolkit-2.22/t/test/dir/sub_one/foo
Template-Toolkit-2.22/t/test/dir/sub_two/
Template-Toolkit-2.22/t/test/dir/sub_two/waz.html
Template-Toolkit-2.22/t/test/dir/sub_two/wiz.html
Template-Toolkit-2.22/t/test/dir/xyzfile
Template-Toolkit-2.22/t/test/lib/
Template-Toolkit-2.22/t/test/lib/after
Template-Toolkit-2.22/t/test/lib/badrawperl
Template-Toolkit-2.22/t/test/lib/barfed
Template-Toolkit-2.22/t/test/lib/before
Template-Toolkit-2.22/t/test/lib/blockdef
Template-Toolkit-2.22/t/test/lib/chomp
Template-Toolkit-2.22/t/test/lib/config
Template-Toolkit-2.22/t/test/lib/content
Template-Toolkit-2.22/t/test/lib/default
Template-Toolkit-2.22/t/test/lib/dos_newlines
Template-Toolkit-2.22/t/test/lib/error
Template-Toolkit-2.22/t/test/lib/footer
Template-Toolkit-2.22/t/test/lib/header
Template-Toolkit-2.22/t/test/lib/header.tt2
Template-Toolkit-2.22/t/test/lib/incblock
Template-Toolkit-2.22/t/test/lib/inner
Template-Toolkit-2.22/t/test/lib/menu
Template-Toolkit-2.22/t/test/lib/one/
Template-Toolkit-2.22/t/test/lib/one/foo
Template-Toolkit-2.22/t/test/lib/outer
Template-Toolkit-2.22/t/test/lib/process
Template-Toolkit-2.22/t/test/lib/README
Template-Toolkit-2.22/t/test/lib/simple2
Template-Toolkit-2.22/t/test/lib/trimme
Template-Toolkit-2.22/t/test/lib/two/
Template-Toolkit-2.22/t/test/lib/two/bar
Template-Toolkit-2.22/t/test/lib/two/foo
Template-Toolkit-2.22/t/test/lib/udata1
Template-Toolkit-2.22/t/test/lib/udata2
Template-Toolkit-2.22/t/test/lib/warning
Template-Toolkit-2.22/t/test/plugin/
Template-Toolkit-2.22/t/test/plugin/MyPlugs/
Template-Toolkit-2.22/t/test/plugin/MyPlugs/Bar.pm
Template-Toolkit-2.22/t/test/plugin/MyPlugs/Baz.pm
Template-Toolkit-2.22/t/test/plugin/MyPlugs/Foo.pm
Template-Toolkit-2.22/t/test/pod/
Template-Toolkit-2.22/t/test/pod/test1.pod
Template-Toolkit-2.22/t/test/src/
Template-Toolkit-2.22/t/test/src/bar/
Template-Toolkit-2.22/t/test/src/bar/baz
Template-Toolkit-2.22/t/test/src/bar/baz.txt
Template-Toolkit-2.22/t/test/src/baz
Template-Toolkit-2.22/t/test/src/benchmark
Template-Toolkit-2.22/t/test/src/blam
Template-Toolkit-2.22/t/test/src/complex
Template-Toolkit-2.22/t/test/src/divisionbyzero
Template-Toolkit-2.22/t/test/src/evalperl
Template-Toolkit-2.22/t/test/src/foo
Template-Toolkit-2.22/t/test/src/foobar
Template-Toolkit-2.22/t/test/src/golf
Template-Toolkit-2.22/t/test/src/leak1
Template-Toolkit-2.22/t/test/src/leak2
Template-Toolkit-2.22/t/test/src/metadata
Template-Toolkit-2.22/t/test/src/mywrap
Template-Toolkit-2.22/t/test/src/README
Template-Toolkit-2.22/t/test/src/recurse
Template-Toolkit-2.22/t/test/tmp/
Template-Toolkit-2.22/t/test/tmp/README
Template-Toolkit-2.22/t/text.t
Template-Toolkit-2.22/t/throw.t
Template-Toolkit-2.22/t/tiedhash.t
Template-Toolkit-2.22/t/try.t
Template-Toolkit-2.22/t/unicode.t
Template-Toolkit-2.22/t/url.t
Template-Toolkit-2.22/t/url2.t
Template-Toolkit-2.22/t/vars.t
Template-Toolkit-2.22/t/varsv1.t
Template-Toolkit-2.22/t/view.t
Template-Toolkit-2.22/t/vmethods/
Template-Toolkit-2.22/t/vmethods/hash.t
Template-Toolkit-2.22/t/vmethods/list.t
Template-Toolkit-2.22/t/vmethods/replace.t
Template-Toolkit-2.22/t/vmethods/text.t
Template-Toolkit-2.22/t/while.t
Template-Toolkit-2.22/t/wrap.t
Template-Toolkit-2.22/t/wrapper.t
Template-Toolkit-2.22/t/zz-pmv.t
Template-Toolkit-2.22/t/zz-pod-coverage.t
Template-Toolkit-2.22/t/zz-pod-kwalitee.t
Template-Toolkit-2.22/t/zz-stash-xs-leak.t
Template-Toolkit-2.22/TODO
Template-Toolkit-2.22/xs/
Template-Toolkit-2.22/xs/Makefile.PL
Template-Toolkit-2.22/xs/MANIFEST
Template-Toolkit-2.22/xs/ppport.h
Template-Toolkit-2.22/xs/README
Template-Toolkit-2.22/xs/Stash.xs

  CPAN.pm: Going to build A/AB/ABW/Template-Toolkit-2.22.tar.gz


                    Template Toolkit Version 2.22
                    =============================

Using Unix defaults.
Run 'perl Makefile.PL TT_HELP' for a summary of options.
Accepting defaults automatically (TT_ACCEPT).

Template::Stash::XS
-------------------

The Template::Stash module is a core part of the Template Toolkit, 
implementing the magic for accessing data using the dot notation.

There is a high speed version, Template::Stash::XS, written in C.
This makes the Template Toolkit run about twice as fast as when using
the regular Template::Stash written in Perl.  If you've got a C
compiler on your system then you can elect to have the XS Stash built.
You can also specify that you want to use the XS Stash by default.

Note that as of version 2.15 the XS Stash now supports access to tied
hashes and arrays.

See 'perldoc Template::Config' for further details.

Do you want to build the XS Stash module? [y] y
Do you want to use the XS Stash by default? [y] y

Checking if your kit is complete...
Looks good
Checking if your kit is complete...
Looks good
Writing Makefile for Template::Stash::XS
Writing Makefile for Template

Configuration complete.  You should now run 'make', 'make test' and 
then 'make install'.   See the README file for further information.
cp lib/Template/Manual/Directives.pod blib/lib/Template/Manual/Directives.pod
cp lib/Template/Manual/Views.pod blib/lib/Template/Manual/Views.pod
cp lib/Template/Plugin/HTML.pm blib/lib/Template/Plugin/HTML.pm
cp lib/Template/Stash.pm blib/lib/Template/Stash.pm
cp lib/Template/Context.pm blib/lib/Template/Context.pm
cp lib/Template/Manual/Intro.pod blib/lib/Template/Manual/Intro.pod
cp lib/Template/Modules.pod blib/lib/Template/Modules.pod
cp lib/Template/Plugin/Procedural.pm blib/lib/Template/Plugin/Procedural.pm
cp lib/Template/Plugin/Iterator.pm blib/lib/Template/Plugin/Iterator.pm
cp lib/Template/Tools/ttree.pod blib/lib/Template/Tools/ttree.pod
cp lib/Template/Toolkit.pod blib/lib/Template/Toolkit.pod
cp lib/Template/Plugin/Scalar.pm blib/lib/Template/Plugin/Scalar.pm
cp lib/Template/Namespace/Constants.pm blib/lib/Template/Namespace/Constants.pm
cp lib/Template/Tutorial/Web.pod blib/lib/Template/Tutorial/Web.pod
cp lib/Template/Iterator.pm blib/lib/Template/Iterator.pm
cp lib/Template/Plugin/String.pm blib/lib/Template/Plugin/String.pm
cp lib/Template/Stash/XS.pm blib/lib/Template/Stash/XS.pm
cp lib/Template/Manual.pod blib/lib/Template/Manual.pod
cp lib/Template/View.pm blib/lib/Template/View.pm
cp lib/Template/Manual/Credits.pod blib/lib/Template/Manual/Credits.pod
cp lib/Template/Plugin/Filter.pm blib/lib/Template/Plugin/Filter.pm
cp lib/Template/Manual/Plugins.pod blib/lib/Template/Manual/Plugins.pod
cp lib/Template/Plugin/Dumper.pm blib/lib/Template/Plugin/Dumper.pm
cp lib/Template/Plugin/Date.pm blib/lib/Template/Plugin/Date.pm
cp lib/Template/Manual/VMethods.pod blib/lib/Template/Manual/VMethods.pod
cp lib/Template/Plugin/File.pm blib/lib/Template/Plugin/File.pm
cp lib/Template/Constants.pm blib/lib/Template/Constants.pm
cp lib/Template/Plugin/Assert.pm blib/lib/Template/Plugin/Assert.pm
cp lib/Template/Plugin/Image.pm blib/lib/Template/Plugin/Image.pm
cp lib/Template/Manual/Config.pod blib/lib/Template/Manual/Config.pod
cp lib/Template/Test.pm blib/lib/Template/Test.pm
cp lib/Template.pm blib/lib/Template.pm
cp lib/Template/VMethods.pm blib/lib/Template/VMethods.pm
cp lib/Template/Plugin/Table.pm blib/lib/Template/Plugin/Table.pm
cp lib/Template/Provider.pm blib/lib/Template/Provider.pm
cp lib/Template/Plugin/Format.pm blib/lib/Template/Plugin/Format.pm
cp lib/Template/Plugin/View.pm blib/lib/Template/Plugin/View.pm
cp lib/Template/Stash/Context.pm blib/lib/Template/Stash/Context.pm
cp lib/Template/Directive.pm blib/lib/Template/Directive.pm
cp lib/Template/Plugin/Datafile.pm blib/lib/Template/Plugin/Datafile.pm
cp lib/Template/Plugin/Directory.pm blib/lib/Template/Plugin/Directory.pm
cp lib/Template/Plugin/Wrap.pm blib/lib/Template/Plugin/Wrap.pm
cp lib/Template/Base.pm blib/lib/Template/Base.pm
cp lib/Template/Plugin/Math.pm blib/lib/Template/Plugin/Math.pm
cp lib/Template/Filters.pm blib/lib/Template/Filters.pm
cp lib/Template/Manual/Internals.pod blib/lib/Template/Manual/Internals.pod
cp lib/Template/Plugin/Pod.pm blib/lib/Template/Plugin/Pod.pm
cp lib/Template/Service.pm blib/lib/Template/Service.pm
cp lib/Template/Manual/Variables.pod blib/lib/Template/Manual/Variables.pod
cp lib/Template/Parser.pm blib/lib/Template/Parser.pm
cp lib/Template/Tools/tpage.pod blib/lib/Template/Tools/tpage.pod
cp lib/Template/Plugins.pm blib/lib/Template/Plugins.pm
cp lib/Template/Manual/Syntax.pod blib/lib/Template/Manual/Syntax.pod
cp lib/Template/Tutorial.pod blib/lib/Template/Tutorial.pod
cp lib/Template/Grammar.pm blib/lib/Template/Grammar.pm
cp lib/Template/Plugin.pm blib/lib/Template/Plugin.pm
cp lib/Template/Config.pm blib/lib/Template/Config.pm
cp lib/Template/FAQ.pod blib/lib/Template/FAQ.pod
cp lib/Template/Tools.pod blib/lib/Template/Tools.pod
cp lib/Template/Plugin/CGI.pm blib/lib/Template/Plugin/CGI.pm
cp lib/Template/Manual/Filters.pod blib/lib/Template/Manual/Filters.pod
cp lib/Template/Document.pm blib/lib/Template/Document.pm
cp lib/Template/Plugin/URL.pm blib/lib/Template/Plugin/URL.pm
cp lib/Template/Exception.pm blib/lib/Template/Exception.pm
cp lib/Template/Tutorial/Datafile.pod blib/lib/Template/Tutorial/Datafile.pod
make[1]: Entering directory `/home/bugzilla/.cpan/build/Template-Toolkit-2.22/xs'
/usr/bin/perl /usr/share/perl/5.8.8/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap  Stash.xs > Stash.xsc && mv Stash.xsc Stash.c
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"2.22\" -DXS_VERSION=\"2.22\" -fPIC "-I/usr/lib/perl/5.8/CORE"   Stash.c
In file included from Stash.xs:36:
/usr/lib/perl/5.8/CORE/perl.h:420:24: error: sys/types.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:451:19: error: ctype.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:463:23: error: locale.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:480:20: error: setjmp.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:486:26: error: sys/param.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:491:23: error: stdlib.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:496:23: error: unistd.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:776:23: error: string.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:925:27: error: netinet/in.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:929:26: error: arpa/inet.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:939:25: error: sys/stat.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:961:21: error: time.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:968:25: error: sys/time.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:975:27: error: sys/times.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:982:19: error: errno.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:997:25: error: sys/socket.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:1024:21: error: netdb.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:1127:24: error: sys/ioctl.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:1156:23: error: dirent.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.2.4/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.2.4/include/limits.h:11,
                 from /usr/lib/perl/5.8/CORE/perl.h:1510,
                 from Stash.xs:36:
/usr/lib/gcc/i486-linux-gnu/4.2.4/include/limits.h:122:61: error: limits.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/perl.h:2120,
                 from Stash.xs:36:
/usr/lib/perl/5.8/CORE/handy.h:136:25: error: inttypes.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/perl.h:2284,
                 from Stash.xs:36:
/usr/lib/perl/5.8/CORE/unixish.h:106:21: error: signal.h: No such file or directory
In file included from Stash.xs:36:
/usr/lib/perl/5.8/CORE/perl.h:2421:33: error: pthread.h: No such file or directory
In file included from Stash.xs:36:
/usr/lib/perl/5.8/CORE/perl.h:2423: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜perl_os_threadâ€™
/usr/lib/perl/5.8/CORE/perl.h:2424: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜perl_mutexâ€™
/usr/lib/perl/5.8/CORE/perl.h:2425: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜perl_condâ€™
/usr/lib/perl/5.8/CORE/perl.h:2426: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜perl_keyâ€™
In file included from /usr/lib/perl/5.8/CORE/iperlsys.h:51,
                 from /usr/lib/perl/5.8/CORE/perl.h:2733,
                 from Stash.xs:36:
/usr/lib/perl/5.8/CORE/perlio.h:65:19: error: stdio.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/iperlsys.h:51,
                 from /usr/lib/perl/5.8/CORE/perl.h:2733,
                 from Stash.xs:36:
/usr/lib/perl/5.8/CORE/perlio.h:259: error: expected â€˜)â€™ before â€˜*â€™ token
/usr/lib/perl/5.8/CORE/perlio.h:262: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜*â€™ token
/usr/lib/perl/5.8/CORE/perlio.h:265: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜*â€™ token
/usr/lib/perl/5.8/CORE/perlio.h:268: error: expected declaration specifiers or â€˜...â€™ before â€˜FILEâ€™
In file included from /usr/lib/perl/5.8/CORE/perl.h:2747,
                 from Stash.xs:36:
/usr/lib/perl/5.8/CORE/sv.h:389: error: expected specifier-qualifier-list before â€˜DIRâ€™
In file included from /usr/lib/perl/5.8/CORE/op.h:497,
                 from /usr/lib/perl/5.8/CORE/perl.h:2754,
                 from Stash.xs:36:
/usr/lib/perl/5.8/CORE/reentr.h:72:20: error: pwd.h: No such file or directory
/usr/lib/perl/5.8/CORE/reentr.h:75:20: error: grp.h: No such file or directory
/usr/lib/perl/5.8/CORE/reentr.h:85:26: error: crypt.h: No such file or directory
/usr/lib/perl/5.8/CORE/reentr.h:90:27: error: shadow.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/op.h:497,
                 from /usr/lib/perl/5.8/CORE/perl.h:2754,
                 from Stash.xs:36:
/usr/lib/perl/5.8/CORE/reentr.h:612: error: field â€˜_crypt_structâ€™ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:620: error: field â€˜_drand48_structâ€™ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:624: error: field â€˜_grent_structâ€™ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:635: error: field â€˜_hostent_structâ€™ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:654: error: field â€˜_netent_structâ€™ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:669: error: field â€˜_protoent_structâ€™ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:684: error: field â€˜_pwent_structâ€™ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:695: error: field â€˜_servent_structâ€™ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:710: error: field â€˜_spent_structâ€™ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:721: error: field â€˜_gmtime_structâ€™ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:724: error: field â€˜_localtime_structâ€™ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:771: error: field â€˜_random_structâ€™ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:772: error: expected specifier-qualifier-list before â€˜int32_tâ€™
In file included from /usr/lib/perl/5.8/CORE/perl.h:2756,
                 from Stash.xs:36:
/usr/lib/perl/5.8/CORE/av.h:13: error: expected specifier-qualifier-list before â€˜ssize_tâ€™
In file included from /usr/lib/perl/5.8/CORE/perl.h:2759,
                 from Stash.xs:36:
/usr/lib/perl/5.8/CORE/scope.h:232: error: expected specifier-qualifier-list before â€˜sigjmp_bufâ€™
In file included from Stash.xs:36:
/usr/lib/perl/5.8/CORE/perl.h:2931: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜getuidâ€™
/usr/lib/perl/5.8/CORE/perl.h:2932: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜geteuidâ€™
/usr/lib/perl/5.8/CORE/perl.h:2933: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜getgidâ€™
/usr/lib/perl/5.8/CORE/perl.h:2934: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜getegidâ€™
In file included from Stash.xs:36:
/usr/lib/perl/5.8/CORE/perl.h:3238:22: error: math.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/perl.h:3881,
                 from Stash.xs:36:
/usr/lib/perl/5.8/CORE/thrdvar.h:85: error: field â€˜Tstatbufâ€™ has incomplete type
/usr/lib/perl/5.8/CORE/thrdvar.h:86: error: field â€˜Tstatcacheâ€™ has incomplete type
/usr/lib/perl/5.8/CORE/thrdvar.h:91: error: field â€˜Ttimesbufâ€™ has incomplete type
In file included from /usr/lib/perl/5.8/CORE/perl.h:3883,
                 from Stash.xs:36:
/usr/lib/perl/5.8/CORE/intrpvar.h:66: error: expected specifier-qualifier-list before â€˜time_tâ€™
In file included from /usr/lib/perl/5.8/CORE/perl.h:3950,
                 from Stash.xs:36:
/usr/lib/perl/5.8/CORE/proto.h:128: error: expected declaration specifiers or â€˜...â€™ before â€˜mode_tâ€™
/usr/lib/perl/5.8/CORE/proto.h:128: error: expected declaration specifiers or â€˜...â€™ before â€˜uid_tâ€™
/usr/lib/perl/5.8/CORE/proto.h:297: error: expected declaration specifiers or â€˜...â€™ before â€˜off64_tâ€™
/usr/lib/perl/5.8/CORE/proto.h:299: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜Perl_do_sysseekâ€™
/usr/lib/perl/5.8/CORE/proto.h:300: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜Perl_do_tellâ€™
/usr/lib/perl/5.8/CORE/proto.h:411: error: expected declaration specifiers or â€˜...â€™ before â€˜gid_tâ€™
/usr/lib/perl/5.8/CORE/proto.h:411: error: expected declaration specifiers or â€˜...â€™ before â€˜uid_tâ€™
/usr/lib/perl/5.8/CORE/proto.h:736: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜Perl_my_forkâ€™
/usr/lib/perl/5.8/CORE/proto.h:1020: error: expected declaration specifiers or â€˜...â€™ before â€˜pid_tâ€™
/usr/lib/perl/5.8/CORE/proto.h:1300: error: expected declaration specifiers or â€˜...â€™ before â€˜pid_tâ€™
/usr/lib/perl/5.8/CORE/proto.h:1456: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜*â€™ token
/usr/lib/perl/5.8/CORE/proto.h:2002: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜Perl_PerlIO_readâ€™
/usr/lib/perl/5.8/CORE/proto.h:2003: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜Perl_PerlIO_writeâ€™
/usr/lib/perl/5.8/CORE/proto.h:2004: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜Perl_PerlIO_unreadâ€™
/usr/lib/perl/5.8/CORE/proto.h:2005: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜Perl_PerlIO_tellâ€™
/usr/lib/perl/5.8/CORE/proto.h:2006: error: expected declaration specifiers or â€˜...â€™ before â€˜off64_tâ€™
In file included from /usr/lib/perl/5.8/CORE/perl.h:3988,
                 from Stash.xs:36:
/usr/lib/perl/5.8/CORE/perlvars.h:31: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜PL_thr_keyâ€™
/usr/lib/perl/5.8/CORE/perlvars.h:48: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜PL_op_mutexâ€™
/usr/lib/perl/5.8/CORE/perlvars.h:52: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜PL_dollarzero_mutexâ€™
/usr/lib/perl/5.8/CORE/perl.h:4485:24: error: sys/ipc.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:4486:24: error: sys/sem.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:4611:24: error: sys/file.h: No such file or directory
In file included from Stash.xs:40:
/usr/lib/perl/5.8/CORE/XSUB.h:101:1: warning: "dAX" redefined
In file included from Stash.xs:39:
ppport.h:3885:1: warning: this is the location of the previous definition
In file included from Stash.xs:40:
/usr/lib/perl/5.8/CORE/XSUB.h:103:1: warning: "dAXMARK" redefined
In file included from Stash.xs:39:
ppport.h:3895:1: warning: this is the location of the previous definition
In file included from Stash.xs:40:
/usr/lib/perl/5.8/CORE/XSUB.h:118:1: warning: "dXSTARG" redefined
In file included from Stash.xs:39:
ppport.h:3892:1: warning: this is the location of the previous definition
In file included from /usr/lib/perl/5.8/CORE/perlapi.h:38,
                 from /usr/lib/perl/5.8/CORE/XSUB.h:349,
                 from Stash.xs:40:
/usr/lib/perl/5.8/CORE/intrpvar.h:66: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜*â€™ token
/usr/lib/perl/5.8/CORE/intrpvar.h:237: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜*â€™ token
/usr/lib/perl/5.8/CORE/intrpvar.h:238: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜*â€™ token
/usr/lib/perl/5.8/CORE/intrpvar.h:239: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜*â€™ token
/usr/lib/perl/5.8/CORE/intrpvar.h:240: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜*â€™ token
In file included from /usr/lib/perl/5.8/CORE/perlapi.h:39,
                 from /usr/lib/perl/5.8/CORE/XSUB.h:349,
                 from Stash.xs:40:
/usr/lib/perl/5.8/CORE/perlvars.h:31: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜*â€™ token
/usr/lib/perl/5.8/CORE/perlvars.h:48: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜*â€™ token
/usr/lib/perl/5.8/CORE/perlvars.h:52: error: expected â€˜=â€™, â€˜,â€™, â€˜;â€™, â€˜asmâ€™ or â€˜__attribute__â€™ before â€˜*â€™ token
Stash.xs: In function â€˜dotopâ€™:
Stash.xs:364: warning: incompatible implicit declaration of built-in function â€˜snprintfâ€™
Stash.xs:367: warning: incompatible implicit declaration of built-in function â€˜strstrâ€™
Stash.xs: In function â€˜find_perl_opâ€™:
Stash.xs:931: warning: incompatible implicit declaration of built-in function â€˜strlenâ€™
make[1]: *** [Stash.o] Error 1
make[1]: Leaving directory `/home/bugzilla/.cpan/build/Template-Toolkit-2.22/xs'
make: *** [subdirs] Error 2
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
```

---

### Post by munky99999 on 2009-12-04
Looks like the make file is bad. Which is odd because 3.4.4 is the latest stable.

You could go with what's in the repos. Which is fairly older. 3.2ish.


You might also want to try to get perl 5.8 into the folders asked. Maybe you dont even have perl? Not sure.

sudo apt-get install perl

---

### Post by david_vanwoensel on 2009-12-07
Thanks for getting back to me.
Yes I have perl installed. This is what comes out of the checksetup.pl
```
* This is Bugzilla 3.4.4 on perl 5.8.8
* Running on Linux 2.6.24-26-generic #1 SMP Tue Dec 1 18:37:31 UTC 2009

Checking perl modules...
Checking for              CGI.pm (v3.21)   ok: found v3.48 
Checking for          Digest-SHA (any)     ok: found v5.45 
Checking for            TimeDate (v2.21)   ok: found v2.22 
Checking for            DateTime (v0.28)   ok: found v0.51 
Checking for   DateTime-TimeZone (v0.71)   ok: found v1.05 
Checking for                 DBI (v1.41)   ok: found v1.601 
Checking for    Template-Toolkit (v2.22)    found v2.19 
Checking for          Email-Send (v2.00)   ok: found v2.198 
Checking for          Email-MIME (v1.861)  ok: found v1.902 
Checking for Email-MIME-Encodings (v1.313)  ok: found v1.313 
Checking for Email-MIME-Modifier (v1.442)  ok: found v1.902 
Checking for                 URI (any)     ok: found v1.35 

Checking available perl DBD modules...
Checking for              DBD-Pg (v1.45)    not found 
Checking for           DBD-mysql (v4.00)   ok: found v4.005 
Checking for          DBD-Oracle (v1.19)    not found 

The following Perl modules are optional:
Checking for                  GD (v1.20)   ok: found v2.35 
Checking for               Chart (v1.0)    ok: found v2.4.1 
Checking for         Template-GD (any)     ok: found v1.56 
Checking for          GDTextUtil (any)     ok: found v0.86 
Checking for             GDGraph (any)     ok: found v1.44 
Checking for            XML-Twig (any)     ok: found v3.32 
Checking for          MIME-tools (v5.406)  ok: found v5.425 
Checking for         libwww-perl (any)     ok: found v2.036 
Checking for         PatchReader (v0.9.4)  ok: found v0.9.5 
Checking for          PerlMagick (any)     ok: found v6.3.7 
Checking for           perl-ldap (any)     ok: found v0.39 
Checking for         Authen-SASL (any)     ok: found v2.13 
Checking for          RadiusPerl (any)     ok: found v0.15 
Checking for           SOAP-Lite (v0.710.06) ok: found v0.710.10 
Checking for         HTML-Parser (v3.40)   ok: found v3.56 
Checking for       HTML-Scrubber (any)     ok: found v0.08 
Checking for Email-MIME-Attachment-Stripper (any)     ok: found v1.316 
Checking for         Email-Reply (any)     ok: found v1.202 
Checking for         TheSchwartz (any)     ok: found v1.07 
Checking for      Daemon-Generic (any)     ok: found v0.61 
Checking for            mod_perl (v1.999022)  not found 
***********************************************************************
* REQUIRED MODULES                                                    *
***********************************************************************
* Bugzilla requires you to install some Perl modules which are either *
* missing from your system, or the version on your system is too old. *
* See below for commands to install these modules.                    *
***********************************************************************
* OPTIONAL MODULES                                                    *
***********************************************************************
* Certain Perl modules are not required by Bugzilla, but by           *
* installing the latest version you gain access to additional         *
* features.                                                           *
*                                                                     *
* The optional modules you do not have installed are listed below,    *
* with the name of the feature they enable. Below that table are the  *
* commands to install each module.                                    *
***********************************************************************
* MODULE NAME * ENABLES FEATURE(S)                                    *
***********************************************************************
*    mod_perl * mod_perl                                              *
***********************************************************************
COMMANDS TO INSTALL OPTIONAL MODULES:

       mod_perl: /usr/bin/perl install-module.pl mod_perl2

COMMANDS TO INSTALL REQUIRED MODULES (You *must* run all these commands
and then re-run checksetup.pl):

    /usr/bin/perl install-module.pl Template

To attempt an automatic install of every required and optional module
with one command, do:

  /usr/bin/perl install-module.pl --all
```

None of the suggested commands work.
I tried downloading the module and building it with make but no success there either. I did this because it says in the beginning of checksetup that "Checking for    Template-Toolkit (v2.22)    found v2.19 "
This probably means that i do have template-toolkit installed but I need a newer version of it? So I downloaded the latest stable version source code from template-toolkit.org, which is 2.22.
After unpacking and makefile, I'm stuck again with the same errors as earlier : no such file or directory.

---

