---
title: "Installing Perl Prerequisites for Monarch"
date: 2010-09-14
forum: Server Platforms
---

### Post by dkirk on 2010-09-14
Hey,

I have an Ubuntu 10.04 server that I have installed nagios on.  I want to install the Monarch web configuration tool but it has some prerequisites.  According to the README file I need to install some perl modules.

Here are the instructions I'm following.  [http://www.question-defense.com/2008/10/24/monarch-configuration-tips-and-tricks-to-manage-nagios-configuration-files](http://www.question-defense.com/2008/10/24/monarch-configuration-tips-and-tricks-to-manage-nagios-configuration-files)

I'm up to ```
cpan> install P/PH/PHISH/XML-LibXML-1.58.tar.gz
```

It gives quite a bit of output, but this is where it seems to go wrong.

```
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/01basic.t ......... ok
t/02parse.t ......... 1/472 Undefined subroutine &XML::LibXML::Common::XML_DTD_NODE called at /root/.cpan/build/XML-LibXML-1.58-o0hqOc/blib/lib/XML/LibXML.pm line 688.
t/02parse.t ......... Dubious, test returned 255 (wstat 65280, 0xff00)
Failed 281/472 subtests
t/03doc.t ........... 1/109 Undefined subroutine &XML::LibXML::Common::XML_DOCUMENT_FRAG_NODE called at t/03doc.t line 57.
t/03doc.t ........... Dubious, test returned 255 (wstat 65280, 0xff00)
Failed 95/109 subtests
t/04node.t .......... 1/130 Undefined subroutine &XML::LibXML::Common::XML_ELEMENT_NODE called at t/04node.t line 31.
t/04node.t .......... Dubious, test returned 255 (wstat 65280, 0xff00)
Failed 129/130 subtests
t/05text.t .......... ok
t/06elements.t ...... ok
t/07dtd.t ........... 1/22 Undefined subroutine &XML::LibXML::Common::XML_ENTITY_REF_NODE called at t/07dtd.t line 66.
t/07dtd.t ........... Dubious, test returned 255 (wstat 65280, 0xff00)
Failed 8/22 subtests
t/08findnodes.t ..... ok
t/09xpath.t ......... ok
t/10ns.t ............ 1/22 Undefined subroutine &XML::LibXML::Common::XML_ELEMENT_NODE called at t/10ns.t line 70.
t/10ns.t ............ Dubious, test returned 9 (wstat 2304, 0x900)
Failed 13/22 subtests
t/11memory.t ........ skipped: (no reason given)
t/12html.t .......... ok
t/13dtd.t ........... ok
t/14sax.t ........... 1/48 Undefined subroutine &XML::LibXML::Common::XML_DOCUMENT_NODE called at /root/.cpan/build/XML-LibXML-1.58-o0hqOc/blib/lib/XML/LibXML/SAX/Parser.pm line 46.
t/14sax.t ........... Dubious, test returned 2 (wstat 512, 0x200)
Failed 43/48 subtests
t/15nodelist.t ...... ok
t/16docnodes.t ...... ok
t/17callbacks.t ..... ok
t/18docfree.t ....... ok
t/19encoding.t ...... Bareword "XML_NAMESPACE_DECL" not allowed while "strict subs" in use at /root/.cpan/build/XML-LibXML-1.58-o0hqOc/blib/lib/XML/LibXML.pm line 1081.
BEGIN not safe after errors--compilation aborted at /root/.cpan/build/XML-LibXML-1.58-o0hqOc/blib/lib/XML/LibXML.pm line 1151.
Compilation failed in require at /usr/lib/perl5/XML/LibXML/Common.pm line 28.
BEGIN failed--compilation aborted at /usr/lib/perl5/XML/LibXML/Common.pm line 28.
Compilation failed in require at t/19encoding.t line 33.
BEGIN failed--compilation aborted at t/19encoding.t line 33.
t/19encoding.t ...... Dubious, test returned 9 (wstat 2304, 0x900)
Failed 7/7 subtests
t/20extras.t ........ 1/12 Undefined subroutine &XML::LibXML::Common::XML_DTD_NODE called at /root/.cpan/build/XML-LibXML-1.58-o0hqOc/blib/lib/XML/LibXML.pm line 688.
t/20extras.t ........ Dubious, test returned 255 (wstat 65280, 0xff00)
Failed 11/12 subtests
t/23rawfunctions.t .. ok
t/24c14n.t .......... ok

Test Summary Report
-------------------
t/02parse.t       (Wstat: 65280 Tests: 191 Failed: 0)
  Non-zero exit status: 255
  Parse errors: Bad plan.  You planned 472 tests but ran 191.
t/03doc.t         (Wstat: 65280 Tests: 14 Failed: 0)
  Non-zero exit status: 255
  Parse errors: Bad plan.  You planned 109 tests but ran 14.
t/04node.t        (Wstat: 65280 Tests: 1 Failed: 0)
  Non-zero exit status: 255
  Parse errors: Bad plan.  You planned 130 tests but ran 1.
t/07dtd.t         (Wstat: 65280 Tests: 14 Failed: 0)
  Non-zero exit status: 255
  Parse errors: Bad plan.  You planned 22 tests but ran 14.
t/10ns.t          (Wstat: 2304 Tests: 9 Failed: 0)
  Non-zero exit status: 9
  Parse errors: Bad plan.  You planned 22 tests but ran 9.
t/14sax.t         (Wstat: 512 Tests: 5 Failed: 0)
  Non-zero exit status: 2
  Parse errors: Bad plan.  You planned 48 tests but ran 5.
t/19encoding.t    (Wstat: 2304 Tests: 0 Failed: 0)
  Non-zero exit status: 9
  Parse errors: Bad plan.  You planned 7 tests but ran 0.
t/20extras.t      (Wstat: 65280 Tests: 1 Failed: 0)
  Non-zero exit status: 255
  Parse errors: Bad plan.  You planned 12 tests but ran 1.
Files=22, Tests=503,  2 wallclock secs ( 0.12 usr  0.33 sys +  0.70 cusr  1.05 csys =  2.20 CPU)
Result: FAIL
Failed 8/22 test programs. 0/503 subtests failed.
make: *** [test_dynamic] Error 255
  PHISH/XML-LibXML-1.58.tar.gz
  /usr/bin/make test -- NOT OK
//hint// to see the cpan-testers results for installing this module, try:
  reports PHISH/XML-LibXML-1.58.tar.gz
Warning (usually harmless): 'YAML' not installed, will not store persistent state
Running make install
  make test had returned bad status, won't install without force
Failed during this command:
 PHISH/XML-LibXML-1.58.tar.gz                 : make_test NO

```

I'm a bit stuck.  I don't know the first thing about perl.  Can someone please help me get this installed so I can continue?


Thanks

David Kirk

---

### Post by emazep on 2011-02-25
There is an Ubuntu package for [FONT=Courier New]XML::LibXML[/FONT], just install that and you won't have any problem:
```
sudo apt-get install libxml-libxml-perl
```If you want to install a Perl module via [FONT=Courier New]cpan[/FONT] (as you were doing), which has prerequisites outside of CPAN itself, you have to install those first of course ([FONT=Courier New]libxml2-dev[/FONT] in this case).

Anyway the easiest route is to always look for the Ubuntu package first.

Cheers.

---

