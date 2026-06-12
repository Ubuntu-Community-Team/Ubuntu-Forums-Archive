---
title: "does command-not-found seem slow?"
date: 2009-04-21
forum: The Cafe
---

### Post by ibuclaw on 2009-04-21
Is it just me, or is the python script **command-not-found** just can be unbearably slow at times, especially when you are the type to make persistent typos:
```

[iain@netbook ~]$ time sl
The program 'sl' is currently not installed.  You can install it by typing:
sudo apt-get install sl

real	0m0.930s
user	0m0.720s
sys	0m0.196s

[iain@netbook ~]$ time pat-get install hello
No command 'pat-get' found, did you mean:
 Command 'apt-get' from package 'apt' (main)
pat-get: command not found

real	0m0.868s
user	0m0.684s
sys	0m0.172s

```
And that is **with** the databases loaded into cache... it gets much much worse the first time it loads everything into memory.

But instead of ranting about it, something tells me that I need to write a script just to save my sanity:
```

#!/usr/bin/perl

use warnings;
use strict;
use GDBM_File;

my $VERSION = 0.3;
my $AUTHOR = 'Iain Buclaw';

my $data_path = '/usr/share/command-not-found/programs.d/';
my $shell_call = 0;
my $program;
my @paths;
my @packages;
my @sources;

my %functions = (
    'version' => \&version,
    'h' => \&subhelp,
    'help' => \&subhelp,
);

sub subhelp
{ 
    print "Usage: command-not-found [options] <command-name>\n",
          "Options:\n",
          "  --version             show program's version number and exit\n",
          "  -h, --help            show this help message and exit\n";
    exit 0;
}

sub version
{ 
    print "$VERSION\n";
    exit 0;
}

sub usage
{ 
    print "Usage: command-not-found [options] <command-name>\n\n",
          "command-not-found: error: no such option: $_[0]\n";
    exit -1;
}

sub find_command
{
    return if(&is_installed);
    local *DIR;
    if(opendir(DIR, $data_path))
    {
        for (readdir(DIR))
        {
            if(/\.db$/)
            {
                my $source = $_;
                tie my %db, 'GDBM_File', $data_path.$source, &GDBM_READER, 0644;
                if(defined $db{$program})
                {
                    my @tmp = split /\|/, $db{$program};
                    for my $dbapp (@tmp)
                    {
                        push @packages, $dbapp;
                        push @sources, $source;
                    }
                }
                untie %db;
            }
        }
        closedir(DIR);
        return;
    }
    exit 127;
}

sub is_installed
{
    for (qw "/usr/local/sbin /usr/local/games /usr/local/bin /usr/sbin /usr/games /usr/bin /sbin /bin") {
        push @paths, "$_" if( -e "$_/$program");
    }
    if(scalar @paths) {
        return 1;
    }
    return 0;
}

sub command_not_found
{
    my $release = &get_release;
    if(scalar @packages == 1)
    {
        my $package = shift @packages;
        my $source = shift @sources;
        $source =~ s/^.*\-(.+?)\.db$/$1/;
        print "The program '$program' is currently not installed.  ";
        if($> == 0)
        {
            print "You can install it by typing:\n";
            print "apt-get install $package\n";
        }
        elsif(&can_sudo)
        {
            print "You can install it by typing:\n";
            print "sudo apt-get install $package\n";
        }
        else {
            print "To run '$program' please ask your administrator to install the package '$package'\n";
        }
        if( not source_enabled($source, $release) ) {
            print "You will have to enable the component called '$1'\n";
        }
    }
    elsif(scalar @packages > 1)
    {
        print "The program '$program' can be found in the following packages:\n";
        for my $package(@packages)
        {
            my $source = shift @sources;
            $source =~ s/^.*\-(.+?)\.db$/$1/;    
            if( not source_enabled($source, $release) ) {
                print " * $package  You will have to enable the component called '$source'\n";
            }
            else {
                print " * $package\n";
            }
        }
        if($> == 0) {
            print "Try: apt-get install <selected package>\n";
        }
        elsif(&can_sudo) {
            print "Try: sudo apt-get install <selected package>\n";
        }
        else {
            print "Ask your administrator to install one of them\n";
        }
    }
    exit 0;
}

sub command_found
{
    my @missing;
    if(scalar @paths == 1)
    {
        my $path = shift @paths;
        print "Command '$program' is available in '$path'\n";
        unless($ENV{PATH} =~ /:$path|$path:|^$path$/) {
            push @missing, $path;
        }
    }
    else
    {
        print "Command '$program' is available in the following places\n";
        for my $path(@paths)
        {
            print " * $path/$program\n";
            unless($ENV{PATH} =~ /:$path|$path:|^$path$/) {
                push @missing, $path;
            }
        }
    }
    if(scalar @missing)
    {
        my $path = (scalar @missing > 1) ? join ':', @missing : $missing[0];
        print "The command could not be located because '$path' is not included in the PATH environment variable.\n";
        if($path =~ /sbin/) {
            print "This is most likely caused by the lack of administrative priviledges associated with your user account.\n";
        }
    }
    exit 0;
}

sub get_release
{
    my $release = undef;
    open(RELEASE, '</etc/lsb-release');
    while(<RELEASE>)
    { 
        if($_ =~ /DISTRIB_CODENAME=(.+)/)
        { 
            $release = $1;
            last;
        }
    } 
    close RELEASE;
    return $release;
}

sub can_sudo
{ 
    open GROUPS, "</etc/group";
    my @admin_group = grep /^admin/, <GROUPS>;
    close GROUPS;
    if($admin_group[0] =~ /$ENV{USER}/) { 
        return 1;
    } 
    return 0;
}

sub source_enabled
{
    my($source, $release) = @_[0,1];
    local *DIR;
    if(opendir(DIR, '/var/lib/apt/lists/'))
    { 
        my $count = 0;
        for (readdir(DIR)) { 
            return 1 if(/$release\_$source.*Packages$/);
        }
        closedir(DIR);
    } 
    return 0;
}

while(my $argp = $ARGV[0])
{
    my @argp = split /=/, $argp;
    
    if(not defined $argp[0]) {
        exit 127;
    }
    
    elsif ($argp[0] =~ /^[-]{1,2}(.*)$/)
    { 
        if(defined $functions{$1} and !$shell_call) {
            $functions{$1}->($argp[1]);
        } 
        elsif($1 =~ /^$/) {
            $shell_call++;
        }
        else { 
            usage($argp);
        }
    }
    elsif($shell_call) { 
        $program = $argp;
    }
    shift @ARGV;
}

if(defined $program)
{
    &find_command;
    &command_not_found if(scalar @packages);
    &command_found if(scalar @paths);
}

print STDERR "$program: command not found\n";
exit 127;

```
Yes... it's Perl. ;)

To install this script:
```
install command-not-found ~/.command-not-found
```
Then add this to the bottom of your ~/.bashrc file:
```
# if the command-not-found is installed locally, use it
if [ -x $HOME/.command-not-found ]; then
    function command_not_found_handle {
            # check because c-n-f could've been removed in the meantime
                if [ -x $HOME/.command-not-found ]; then
           /usr/bin/perl $HOME/.command-not-found -- $1
                   return $?
        else
           return 127
        fi
    }
fi

```
And all subsequently opened terminals/sessions will use it.

To uninstall this script:
```
rm ~/.command-not-found
```

If anyone is brave enough, please test this out and tell me if you notice the difference or anything that I may have messed up in the script.

These are my new run-times:
```

[iain@netbook ~]$ time sl
The program 'sl' is currently not installed.  You can install it by typing:
sudo apt-get install sl

real	0m0.073s
user	0m0.048s
sys	0m0.020s

[iain@netbook ~]$ time pat-get install hello
pat-get: command not found

real	0m0.067s
user	0m0.032s
sys	0m0.032s

```

Much much snappier, imo ... albeit with a few features removed here or there.

Regards
Iain

---

