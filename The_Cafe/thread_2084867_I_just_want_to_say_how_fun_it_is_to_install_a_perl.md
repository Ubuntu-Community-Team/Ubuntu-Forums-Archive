---
title: "I just want to say how fun it is to install a perl module"
date: 2012-11-16
forum: The Cafe
---

### Post by fixitdude on 2012-11-16
So I needed a perl "module" (it ain't modular at all) for a program, it is GD.pm

So of course you have to do geeky things to get it...

You have to start up some sort of special terminal that has a command line with all sorts of new wonderful commands.

sudo perl -MCPAN -e shell    <<< THAT'S NOT GEEKY !!!

Why can't I just "sudo perl install GD.pm" and it goes out and gets the 8K file from somewhere, it's a module isn't it?

And now you have to do some really strange stuff at their command line:

install Bundle::CPAN

I am still not at the point of getting my module!!!

Now it starts downloading the entire internet, here's a sample....

SOMEONE NEEDS TO DE-GEEK THIS CRAP!!!! << thanks for letting me rant

```

Installing /usr/local/man/man3/ExtUtils::MM_Darwin.3pm
Installing /usr/local/man/man3/ExtUtils::Mkbootstrap.3pm
Installing /usr/local/man/man3/ExtUtils::MakeMaker::FAQ.3pm
Installing /usr/local/man/man3/ExtUtils::MM_NW5.3pm
Installing /usr/local/man/man3/ExtUtils::MakeMaker.3pm
Installing /usr/local/man/man3/ExtUtils::MM_OS2.3pm
Installing /usr/local/man/man3/CPAN::Meta::Feature.3pm
Installing /usr/local/man/man3/ExtUtils::MM_Unix.3pm
Installing /usr/local/man/man3/ExtUtils::MM_Win32.3pm
Installing /usr/local/man/man3/CPAN::Meta::Spec.3pm
Installing /usr/local/man/man3/CPAN::Meta::History.3pm
Installing /usr/local/man/man3/ExtUtils::MY.3pm
Installing /usr/local/man/man3/ExtUtils::MM_MacOS.3pm
Installing /usr/local/man/man3/ExtUtils::MM_VMS.3pm
Installing /usr/local/man/man3/ExtUtils::MM_BeOS.3pm
Installing /usr/local/man/man3/ExtUtils::MakeMaker::Tutorial.3pm
Installing /usr/local/man/man3/ExtUtils::MM_QNX.3pm
Installing /usr/local/man/man3/CPAN::Meta::Converter.3pm
Installing /usr/local/man/man3/ExtUtils::Command::MM.3pm
Installing /usr/local/man/man3/JSON::PP::Compat5006.3pm
Installing /usr/local/man/man3/ExtUtils::MakeMaker::Config.3pm
Installing /usr/local/man/man3/CPAN::Meta.3pm
Installing /usr/local/man/man3/CPAN::Meta::Prereqs.3pm
Installing /usr/local/man/man3/CPAN::Meta::Validator.3pm
Installing /usr/local/man/man3/ExtUtils::MM_Any.3pm
Installing /usr/local/bin/instmodsh
Appending installation info to /usr/lib/perl/5.14/perllocal.pod
  MSCHWERN/ExtUtils-MakeMaker-6.62.tar.gz
  /usr/bin/make install  -- OK
Running install for module 'Test::Harness'
Running make for O/OV/OVID/Test-Harness-3.25.tar.gz
Fetching with LWP:
[ftp://cpan.cs.utah.edu/CPAN/authors/id/O/OV/OVID/Test-Harness-3.25.tar.gz](ftp://cpan.cs.utah.edu/CPAN/authors/id/O/OV/OVID/Test-Harness-3.25.tar.gz)
Fetching with LWP:
[ftp://cpan.cs.utah.edu/CPAN/authors/id/O/OV/OVID/CHECKSUMS](ftp://cpan.cs.utah.edu/CPAN/authors/id/O/OV/OVID/CHECKSUMS)
Checksum for /home/me/.cpan/sources/authors/id/O/OV/OVID/Test-Harness-3.25.tar.gz ok

  CPAN.pm: Going to build O/OV/OVID/Test-Harness-3.25.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for Test::Harness
Writing MYMETA.yml and MYMETA.json
cp lib/TAP/Parser/Result/Pragma.pm blib/lib/TAP/Parser/Result/Pragma.pm
cp lib/TAP/Parser/Iterator/Array.pm blib/lib/TAP/Parser/Iterator/Array.pm
cp lib/App/Prove/State/Result.pm blib/lib/App/Prove/State/Result.pm
cp lib/TAP/Base.pm blib/lib/TAP/Base.pm
cp lib/TAP/Formatter/Console/ParallelSession.pm blib/lib/TAP/Formatter/Console/ParallelSession.pm
cp lib/TAP/Parser/Result.pm blib/lib/TAP/Parser/Result.pm
cp lib/TAP/Formatter/Console/Session.pm blib/lib/TAP/Formatter/Console/Session.pm
cp lib/TAP/Parser/Scheduler/Job.pm blib/lib/TAP/Parser/Scheduler/Job.pm
cp lib/TAP/Parser/Result/YAML.pm blib/lib/TAP/Parser/Result/YAML.pm
cp lib/TAP/Parser.pm blib/lib/TAP/Parser.pm
cp lib/TAP/Parser/SourceHandler/Handle.pm blib/lib/TAP/Parser/SourceHandler/Handle.pm
cp lib/TAP/Parser/IteratorFactory.pm blib/lib/TAP/Parser/IteratorFactory.pm
cp lib/TAP/Parser/Iterator.pm blib/lib/TAP/Parser/Iterator.pm
cp lib/TAP/Formatter/Color.pm blib/lib/TAP/Formatter/Color.pm
cp lib/TAP/Parser/Iterator/Process.pm blib/lib/TAP/Parser/Iterator/Process.pm
cp lib/TAP/Parser/Grammar.pm blib/lib/TAP/Parser/Grammar.pm
cp HACKING.pod blib/lib/Test/HACKING.pod
cp lib/Test/Harness.pm blib/lib/Test/Harness.pm
cp lib/TAP/Formatter/File/Session.pm blib/lib/TAP/Formatter/File/Session.pm
cp lib/TAP/Formatter/Base.pm blib/lib/TAP/Formatter/Base.pm
cp lib/TAP/Parser/ResultFactory.pm blib/lib/TAP/Parser/ResultFactory.pm
cp lib/TAP/Parser/Utils.pm blib/lib/TAP/Parser/Utils.pm
cp lib/TAP/Parser/Result/Bailout.pm blib/lib/TAP/Parser/Result/Bailout.pm
cp lib/TAP/Object.pm blib/lib/TAP/Object.pm
cp lib/TAP/Parser/Multiplexer.pm blib/lib/TAP/Parser/Multiplexer.pm
cp lib/TAP/Parser/SourceHandler/Perl.pm blib/lib/TAP/Parser/SourceHandler/Perl.pm
cp lib/TAP/Parser/Result/Version.pm blib/lib/TAP/Parser/Result/Version.pm
cp lib/TAP/Parser/YAMLish/Writer.pm blib/lib/TAP/Parser/YAMLish/Writer.pm
cp lib/TAP/Parser/Result/Unknown.pm blib/lib/TAP/Parser/Result/Unknown.pm
cp lib/TAP/Parser/YAMLish/Reader.pm blib/lib/TAP/Parser/YAMLish/Reader.pm
cp lib/TAP/Parser/Scheduler.pm blib/lib/TAP/Parser/Scheduler.pm
cp lib/TAP/Parser/Result/Plan.pm blib/lib/TAP/Parser/Result/Plan.pm
cp lib/TAP/Parser/SourceHandler.pm blib/lib/TAP/Parser/SourceHandler.pm
cp lib/TAP/Parser/SourceHandler/Executable.pm blib/lib/TAP/Parser/SourceHandler/Executable.pm
cp lib/TAP/Parser/Result/Test.pm blib/lib/TAP/Parser/Result/Test.pm
cp lib/App/Prove/State/Result/Test.pm blib/lib/App/Prove/State/Result/Test.pm
cp lib/TAP/Parser/SourceHandler/RawTAP.pm blib/lib/TAP/Parser/SourceHandler/RawTAP.pm
cp lib/TAP/Parser/Source.pm blib/lib/TAP/Parser/Source.pm
cp lib/TAP/Formatter/Console.pm blib/lib/TAP/Formatter/Console.pm
cp lib/TAP/Parser/Iterator/Stream.pm blib/lib/TAP/Parser/Iterator/Stream.pm
cp lib/TAP/Parser/SourceHandler/File.pm blib/lib/TAP/Parser/SourceHandler/File.pm
cp lib/TAP/Harness/Beyond.pod blib/lib/TAP/Harness/Beyond.pod
cp lib/TAP/Formatter/Session.pm blib/lib/TAP/Formatter/Session.pm
cp lib/App/Prove.pm blib/lib/App/Prove.pm
cp lib/App/Prove/State.pm blib/lib/App/Prove/State.pm
cp lib/TAP/Harness.pm blib/lib/TAP/Harness.pm
cp lib/TAP/Formatter/File.pm blib/lib/TAP/Formatter/File.pm
cp lib/TAP/Parser/Aggregator.pm blib/lib/TAP/Parser/Aggregator.pm
cp lib/TAP/Parser/Scheduler/Spinner.pm blib/lib/TAP/Parser/Scheduler/Spinner.pm
cp lib/TAP/Parser/Result/Comment.pm blib/lib/TAP/Parser/Result/Comment.pm
cp bin/prove blib/script/prove
/usr/bin/perl -MExtUtils::MY -e 'MY->fixin(shift)' -- blib/script/prove
Manifying blib/man1/prove.1p
Manifying blib/man3/TAP::Parser::Result::Pragma.3pm
Manifying blib/man3/App::Prove::State::Result.3pm
Manifying blib/man3/TAP::Parser::Iterator::Array.3pm
Manifying blib/man3/TAP::Base.3pm
Manifying blib/man3/TAP::Formatter::Console::ParallelSession.3pm
Manifying blib/man3/TAP::Parser::Result.3pm
Manifying blib/man3/TAP::Formatter::Console::Session.3pm
Manifying blib/man3/TAP::Parser::Result::YAML.3pm
Manifying blib/man3/TAP::Parser::Scheduler::Job.3pm
Manifying blib/man3/TAP::Parser.3pm
Manifying blib/man3/TAP::Parser::SourceHandler::Handle.3pm
Manifying blib/man3/TAP::Parser::IteratorFactory.3pm
Manifying blib/man3/TAP::Parser::Iterator.3pm
Manifying blib/man3/TAP::Formatter::Color.3pm
Manifying blib/man3/TAP::Parser::Iterator::Process.3pm
Manifying blib/man3/TAP::Parser::Grammar.3pm
Manifying blib/man3/Test::HACKING.3pm
Manifying blib/man3/Test::Harness.3pm
Manifying blib/man3/TAP::Formatter::Base.3pm
Manifying blib/man3/TAP::Formatter::File::Session.3pm
Manifying blib/man3/TAP::Parser::Result::Bailout.3pm
Manifying blib/man3/TAP::Parser::Utils.3pm
Manifying blib/man3/TAP::Parser::ResultFactory.3pm
Manifying blib/man3/TAP::Parser::SourceHandler::Perl.3pm
Manifying blib/man3/TAP::Parser::Multiplexer.3pm
Manifying blib/man3/TAP::Object.3pm
Manifying blib/man3/TAP::Parser::YAMLish::Writer.3pm
Manifying blib/man3/TAP::Parser::Result::Version.3pm
Manifying blib/man3/TAP::Parser::Result::Unknown.3pm
Manifying blib/man3/TAP::Parser::YAMLish::Reader.3pm
Manifying blib/man3/TAP::Parser::Scheduler.3pm
Manifying blib/man3/TAP::Parser::Result::Plan.3pm
Manifying blib/man3/TAP::Parser::SourceHandler.3pm
Manifying blib/man3/TAP::Parser::SourceHandler::Executable.3pm
Manifying blib/man3/TAP::Parser::Result::Test.3pm
Manifying blib/man3/App::Prove::State::Result::Test.3pm
Manifying blib/man3/TAP::Parser::SourceHandler::RawTAP.3pm
Manifying blib/man3/TAP::Formatter::Console.3pm
Manifying blib/man3/TAP::Parser::Source.3pm
Manifying blib/man3/TAP::Parser::Result::Comment.3pm
Manifying blib/man3/TAP::Parser::Iterator::Stream.3pm
Manifying blib/man3/TAP::Parser::SourceHandler::File.3pm
Manifying blib/man3/TAP::Harness::Beyond.3pm
Manifying blib/man3/TAP::Formatter::Session.3pm
Manifying blib/man3/App::Prove::State.3pm
Manifying blib/man3/App::Prove.3pm
Manifying blib/man3/TAP::Harness.3pm
Manifying blib/man3/TAP::Formatter::File.3pm
Manifying blib/man3/TAP::Parser::Aggregator.3pm
Manifying blib/man3/TAP::Parser::Scheduler::Spinner.3pm
  OVID/Test-Harness-3.25.tar.gz
  /usr/bin/make -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-Iblib/lib" "-Iblib/arch" "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t t/compat/*.t
t/000-load.t .................... 1/97 # Testing Test::Harness 3.25, Perl 5.014002, /usr/bin/perl
t/000-load.t .................... ok     
t/aggregator.t .................. ok     
t/bailout.t ..................... ok     
t/base.t ........................ ok     
t/callbacks.t ................... ok     
t/compat/env.opts.t ............. ok     
t/compat/env.t .................. ok   
t/compat/failure.t .............. ok   
t/compat/inc-propagation.t ...... ok   
t/compat/inc_taint.t ............ ok   
t/compat/nonumbers.t ............ ok   
t/compat/regression.t ........... ok   
t/compat/subclass.t ............. ok   
t/compat/switches.t ............. ok   
t/compat/test-harness-compat.t .. ok       
t/compat/version.t .............. ok   
t/console.t ..................... ok   
t/errors.t ...................... ok     
t/file.t ........................ ok     
t/glob-to-regexp.t .............. ok     
t/grammar.t ..................... ok     
t/harness-bailout.t ............. ok   
t/harness-subclass.t ............ ok     
t/harness.t ..................... ok       
t/iterator_factory.t ............ ok     
t/iterators.t ................... ok     
t/multiplexer.t ................. ok    
t/nested.t ...................... ok   
t/nofork-mux.t .................. ok    
t/nofork.t ...................... ok   
t/nowarn.t ...................... ok   
t/object.t ...................... ok   
t/parse.t ....................... ok       
t/parser-config.t ............... ok   
t/parser-subclass.t ............. ok     
t/perl5lib.t .................... ok   
t/premature-bailout.t ........... ok     
t/process.t ..................... ok     
t/prove.t ....................... ok         
t/proveenv.t .................... ok   
t/proverc.t ..................... ok   
t/proverun.t .................... ok   
t/proveversion.t ................ ok   
t/regression.t .................. ok      
t/results.t ..................... ok       
t/scheduler.t ................... ok       
t/source.t ...................... ok     
t/source_handler.t .............. ok     
t/spool.t ....................... ok   
t/state.t ....................... ok     
t/state_results.t ............... ok     
t/streams.t ..................... ok     
t/taint.t ....................... ok   
t/testargs.t .................... ok     
t/unicode.t ..................... ok    
t/utils.t ....................... ok     
t/yamlish-output.t .............. ok   
t/yamlish-writer.t .............. ok       
t/yamlish.t ..................... ok       
All tests successful.
Files=59, Tests=11762, 29 wallclock secs ( 3.90 usr  0.31 sys + 12.42 cusr  1.68 csys = 18.31 CPU)
Result: PASS
  OVID/Test-Harness-3.25.tar.gz
  /usr/bin/make test -- OK
Running make install
Installing /usr/local/share/perl/5.14.2/Test/HACKING.pod
Installing /usr/local/share/perl/5.14.2/Test/Harness.pm
Installing /usr/local/share/perl/5.14.2/TAP/Base.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser.pm
Installing /usr/local/share/perl/5.14.2/TAP/Object.pm
Installing /usr/local/share/perl/5.14.2/TAP/Harness.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Result.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/IteratorFactory.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Iterator.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Grammar.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/ResultFactory.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Utils.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Multiplexer.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Scheduler.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/SourceHandler.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Source.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Aggregator.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Result/Pragma.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Result/YAML.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Result/Bailout.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Result/Version.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Result/Unknown.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Result/Plan.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Result/Test.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Result/Comment.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Iterator/Array.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Iterator/Process.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Iterator/Stream.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Scheduler/Job.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/Scheduler/Spinner.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/SourceHandler/Handle.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/SourceHandler/Perl.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/SourceHandler/Executable.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/SourceHandler/RawTAP.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/SourceHandler/File.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/YAMLish/Writer.pm
Installing /usr/local/share/perl/5.14.2/TAP/Parser/YAMLish/Reader.pm
Installing /usr/local/share/perl/5.14.2/TAP/Formatter/Color.pm
Installing /usr/local/share/perl/5.14.2/TAP/Formatter/Base.pm
Installing /usr/local/share/perl/5.14.2/TAP/Formatter/Console.pm
Installing /usr/local/share/perl/5.14.2/TAP/Formatter/Session.pm
Installing /usr/local/share/perl/5.14.2/TAP/Formatter/File.pm
Installing /usr/local/share/perl/5.14.2/TAP/Formatter/Console/ParallelSession.pm
Installing /usr/local/share/perl/5.14.2/TAP/Formatter/Console/Session.pm
Installing /usr/local/share/perl/5.14.2/TAP/Formatter/File/Session.pm
Installing /usr/local/share/perl/5.14.2/TAP/Harness/Beyond.pod
Installing /usr/local/share/perl/5.14.2/App/Prove.pm
Installing /usr/local/share/perl/5.14.2/App/Prove/State.pm
Installing /usr/local/share/perl/5.14.2/App/Prove/State/Result.pm
Installing /usr/local/share/perl/5.14.2/App/Prove/State/Result/Test.pm
Installing /usr/local/man/man1/prove.1p
Installing /usr/local/man/man3/TAP::Parser::Result::Pragma.3pm
Installing /usr/local/man/man3/App::Prove::State::Result.3pm
Installing /usr/local/man/man3/TAP::Parser::Iterator::Array.3pm
Installing /usr/local/man/man3/TAP::Base.3pm
Installing /usr/local/man/man3/TAP::Formatter::Console::ParallelSession.3pm
Installing /usr/local/man/man3/TAP::Parser::Result.3pm
Installing /usr/local/man/man3/TAP::Formatter::Console::Session.3pm
Installing /usr/local/man/man3/TAP::Parser::Result::YAML.3pm
Installing /usr/local/man/man3/TAP::Parser::Scheduler::Job.3pm
Installing /usr/local/man/man3/TAP::Parser.3pm
Installing /usr/local/man/man3/TAP::Parser::SourceHandler::Handle.3pm

```

---

### Post by VooDooSyxx on 2012-11-16
Instead of ranting and expecting a programming language of all things, to be rewritten just to be user friendly, why not just install the package that's already in the Ubuntu repos?

```

sudo apt-get install libgd-gd2-perl

```

---

