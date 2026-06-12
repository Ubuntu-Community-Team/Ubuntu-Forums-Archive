---
title: "how come..."
date: 2008-03-10
forum: Virtualisation
---

### Post by niko123 on 2008-03-10
when i open vmware server through the console with the command...
```

vmware

```

i get the following out put...

```

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

```

and when i do type /usr/bin/vmware-config.pl it says that i have no such file or directory...and as of now....the only way ive been able to fix is is if i sudo remove the vmware server...then sudo install it agian..

can anyone help me with this problem

thanks!

---

### Post by fjgaude on 2008-03-10
Were you able to at least once run the .pl file?

---

### Post by niko123 on 2008-03-10
no....

but as i was looking through my filesystem....i found that the vmware-config.pl icon is not in /usr/bin/vmware-config.pl

but i do see the icon in /usr/vmware-config.pl and when i type 
```

/usr/vmware-config.pl.

```

is that normal...?

and when i type
```

gedit /usr/bin/vmware-config.pl

```
i recive a empty script....

but when i type
```

/usr/vmware-config.pl

```
i recive this
```

#!/usr/bin/perl -w
# If your copy of perl is not in /usr/bin, please adjust the line above.
#
# Copyright 1998 VMware, Inc.  All rights reserved.
#
# Host configurator for VMware

use strict;

# Use Config module to update VMware host-wide configuration file
# BEGINNING_OF_CONFIG_DOT_PM
#!/usr/bin/perl

###
### TODOs:
###  config file hierarchies
###  open/close/check file
###  error handling
###  config file checker
###  pretty print should print not present devices not in misc
###

use strict;
package VMware::Config;

my %PREF;

#$PREF{'commentChanges'} = 1;

sub new() {
  my $proto = shift;
  my $class = ref($proto) || $proto;
  my $self = $proto->create();
  bless($self, $class);
  return($self);
}

sub create {
  my $self = {};
  $self->{db} = {};
  $self->{tr} = 1;
  return($self);  
}

sub preserve_case($) {
  my $self = shift;
  my $preserve = shift;
  $self->{tr} = !$preserve;
}

sub clear() {
  my $self = {};
  $self->{db} = {};
}

sub readin($) {
  my $self = shift;
  my ($file) = @_;

  my $text = "";
  
  my @stat = stat($file);
  $self->{timestamp} = $stat[9];

  open(CFG, "< $file") || return undef;
  
  while (<CFG>) {
    $text = $text . $_;
  }
  
  close(CFG);

  my $ret = $self->parse($text);
  if (!defined($ret)) {
    return undef;
  }

  $self->{file} = $file;
  $self->{text} = $text;

  return 1;
}

sub writeout($) {
  my $self = shift;
  my ($file) = @_;

  if (!defined($file)) {
    $file = $self->{file};
  }

  open(CFG, "> $file") || return undef;
  print CFG $self->update($self->{text});
  close(CFG);

  return 1;
}

sub overwrite($$) {
  my $self = shift;
  my($orig, $file) = @_;
  
  if (!defined($file)) {
    $file = $orig->{file};
  }
  
  open(CFG, "> $file") || return undef;
  print CFG $self->update($orig->{text});
  close(CFG);

  return 1;  
}

sub pretty_overwrite {
  my $self = shift;
  my($file) = @_;
  
  if (!defined($file)) {
    $file = $self->{file};
  }
  
  open(CFG, "> $file") || return undef;
  print CFG $self->pretty_print();
  close(CFG);

  return 1;  
}

sub parse($) {
  my $self = shift;
  my ($text) = @_;
  my(@lines, $line, $num);
  
  @lines = split(/\n/, $text);
  $num = 1;
  
  foreach $line (@lines) {
    my($status, $name, $value, $start, $end) = $self->parse_line($line);
    if (!defined($status)) {
      $self->clear();
      # syntax error on line $num
      return undef;
    } elsif ($status == 1) {
      if ($self->{tr}) {
        $name =~ tr/A-Z/a-z/;
      }
      $self->{db}{$name}{value} = $value;
      $self->{db}{$name}{modified} = 0;
      $self->{db}{$name}{mark} = 0;
    } elsif ($status == 0) {
      # noop
    } else {
      $self->clear();
      # internal error
      return undef;
    }
    $num++;
  }
  
  return 1;
}

sub timestamp() {
  my $self = shift;
  return $self->{timestamp};
}

sub get() {
  my $self = shift;
  my($name, $default) = @_;
  if ($self->{tr}) {
    $name =~ tr/A-Z/a-z/;
  }
  if (defined($self->{db}{$name})) {
    $self->{db}{$name}{mark} = 1;
    return $self->{db}{$name}{value};
  } else {
    return $default;
  }
}
        
sub get_bool() {
  my $self = shift;
  my($name, $default) = @_;
  my $val = $self->get($name);
  if (!defined($val)) {
    $val = $default;
  }
  if ($val =~ /TRUE|1|Y|YES/i) {
    $val = 1;
  } else {
    $val = 0;
  }
  return $val;
}
        
sub set($$) {
  my $self = shift;
  my($name, $value) = @_;
  if ($self->{tr}) {
    $name =~ tr/A-Z/a-z/;
  }
  $self->{db}{$name}{value} = $value;
  $self->{db}{$name}{modified} = 1;
  $self->{db}{$name}{mark} = 0;
}

sub remove($) {
  my $self = shift;
  my($name) = @_;
  if ($self->{tr}) {
    $name =~ tr/A-Z/a-z/;
  }
  delete $self->{db}{$name};
}

sub list($) {
  my $self = shift;
  my($pattern) = @_;
  return sort(grep(/$pattern/, keys(%{$self->{db}})));
}

sub device_list {
  my $self = shift;
  my($name, $pattern, $show_all) = @_;
  my($dev, $val, %present);

  $show_all = 0 if (!defined($show_all));

  foreach $_ (keys(%{$self->{db}})) {
    if (/$name($pattern)\.present/) {
      $dev = $name . $1;
      $val = $self->get_bool("$dev.present");
      if ($show_all || !defined($val) || ($val)) {
        $present{$dev} = 1;
      }
    }
  }

  return sort(keys(%present));
}

sub update($) {
  my $self = shift;
  my ($text) = @_;
  my $out = "";
  my($line, $name);
  
  my @lines;
  if (defined($text)) {
    @lines = split(/\n/, $text);
  }
  my $num = 1;

  $self->unmark_all();
  
  foreach $line (@lines) {
    my($status, $name, $value, $start, $end) = $self->parse_line($line);

    if (defined($name)) {
      if ($self->{tr}) {
        $name =~ tr/A-Z/a-z/;
      }
    }

    ###
    ### five cases
    ###
    ###   1. deleted
    ###   2. modified
    ###   3. unmodified
    ###   4. comment or blank line
    ###   5. new (handled at the end)
    ###

    $line = $line . "\n";

    if (!defined($status)) {
      # XXX syntax error on line $num
      return undef;
      
    } elsif ($status == 1) {
      if (!defined($self->{db}{$name})) {
        ###
        ### Case 1. removed
        ###
        
        if (defined($PREF{'commentChanges'})) {
          $line = "# " . $line;
        } else {
          $line = "";
        }
        
      } else {
        $self->mark($name);

        if ($self->{db}{$name}{value} ne $value) {  
          ###
          ### Case 2. modified
          ###
          
          my $newline = substr($line, 0, $start) 
            . "\"" . $self->{db}{$name}{value} . "\"" . substr($line, $end);
          
          if (defined($PREF{'commentChanges'})) {
            $line = "# " . $line . $newline;
          } else {
            $line = $newline;
          }
          
        } else {
          ###
          ### Case 3. unmodified
          ###
        }
      }

    } elsif ($status == 0) {
      ###
      ### Case 4. comment or blank line
      ###
      
    } else {
      # XXX internal error: parse_line returned unknown status \"$status\"
      return undef;
    }
    
    $out = $out . "$line";
    $num++;
  }

  ###
  ### Case 5. new entries
  ###

  $out = $out . $self->print_unmarked();

  return $out;
}

sub dump_all() {
  my $self = shift;
  my $out = "";
  my $name;
  
  foreach $name (keys(%{$self->{db}})) {
    $out = $out . "$name = \"$self->{db}{$name}{value}\"\n";
  }
  
  return $out;
}

sub pretty_print($) {
  my $self = shift;
  my($templ) = @_;
  my $out = "";
  my $sec;

  $self->unmark_all();
  
  foreach $sec (@{$templ}) {  
    $out = $out . $self->print_section($sec, "");
  }
  
  $out = $out . "###\n### Misc.\n###\n\n";
  $out = $out . $self->print_unmarked();

  return $out;
}

sub print_section {
  my $self = shift;
  my($sec, $prefix) = @_;
  my $out = "";

  my @list;
  my $dev;
  
  if (defined($sec->{header})) {
    $out = $out . "###\n### $sec->{header}\n###\n\n";
  }
  
  ## name is here for compatibility, it should go away soon.
  my $name = defined($sec->{name}) ? $sec->{name} : "";

  if (defined($sec->{pattern})) {
    @list = $self->device_list($prefix . $name, $sec->{pattern}, 1);
    foreach $dev (@list) {
      if (defined($sec->{title})) {
        $out = $out . sprintf("# $sec->{title}\n\n", $dev);
      }
      $out = $out . $self->print_values("$dev", $sec->{values});
      if (defined($sec->{sublist})) {
        $out = $out . $self->print_section($sec->{sublist}, "$dev");
      }
    }
  } else {
    if (defined($sec->{values})) {
      $out = $out . $self->print_values($prefix . $name, $sec->{values});
    } else {
      $out = $out . $self->print_value($prefix . $name, "is not set");
      $out = $out . "\n";
    }
  }

  return $out;
}

sub print_values {
  my $self = shift;
  my($name, $vars) = @_;
  my $var;

  my $out = "";
  
   foreach $var (@{$vars}) {
     my $v = ($name ne "") ? "$name.$var" : $var;
     $out = $out . $self->print_value($v);
  }

  $out = $out . "\n";

  return $out;
}

sub print_value {
  my $self = shift;
  my($name, $notset) = @_;
  my $val = $self->get($name);
  if (defined($val)) {
    $self->mark($name);
    return "$name = \"$val\"\n";
  } elsif (defined($notset)) {
    return "# $name $notset\n";
  }
}

sub mark($) {
  my $self = shift;
  my($name) = @_;
  if ($self->{tr}) {
    $name =~ tr/A-Z/a-z/;
  }
  $self->{db}{$name}{mark} = 1;
}

sub unmark_all() {
  my $self = shift;
  my $name;
  foreach $name (keys %{$self->{db}}) {
    $self->{db}{$name}{mark} = 0;
  }
}

sub get_unmarked() {
  my $self = shift;
  my $name;
  my @list = ();
  foreach $name (keys %{$self->{db}}) {
    if (!$self->{db}{$name}{mark}) {
      push(@list, $name);
    }
  }
  return @list;
}

sub print_unmarked() {
  my $self = shift;
  my @unmarked = $self->get_unmarked();
  my $out = "";
  my $name;
  
  foreach $name (@unmarked) {
    $out = $out . "$name = \"$self->{db}{$name}{value}\"\n";
  }

  return $out;
}

sub parse_line($) {
  my $self = shift;
  ($_) = @_;

  if (/^\s*(\#.*)?$/) {
    return (0);
  } elsif (/^((\s*(\S+)\s*=\s*)(([\"]([^\"]*)[\"])|(\S+)))\s*(\#.*)?$/) {
    my $prefix1 = $2;
    my $prefix2 = $1;
    my $name = $3;
    my $value;
    if (defined($6)) {
      $value = $6;
    } else {
      $value = $7;
    }

    return (1, $name, $value, length($prefix1), length($prefix2));
  } 

  return (undef);  
}



1;

# END_OF_CONFIG_DOT_PM

use Config;


# Constants
my $cKernelModuleDir = '/lib/modules';
my $cTmpDirPrefix = 'vmware-config';
my $cVmnixVersion = '@@VMNIXVERSION@@';
my $cConnectSocketDir = '/var/run/vmware';
my $machine = 'host';
my $os = 'host';
if (vmware_product() eq 'server') {
  $machine = 'machine';
  $os = "Console OS";
}
my $cServices = '/etc/services';
my $cMarkerBegin = "# Beginning of the block added by the VMware software\n";
my $cMarkerEnd = "# End of the block added by the VMware software\n";

my $cConfiguratorFileName = 'vmware-config.pl';
my $cNICAlias = 'vmnics';

if (vmware_product() eq 'tools-for-linux' ||
    vmware_product() eq 'tools-for-freebsd' ||
    vmware_product() eq 'tools-for-solaris') {
  $cConfiguratorFileName = 'vmware-config-tools.pl';
}

my $cModulesBuildEnv = ' you can install the driver by running '
                       . $cConfiguratorFileName
                       . ' again after making sure that gcc, binutils, make '
                       . 'and the kernel sources for your running kernel are '
                       . 'installed on your machine. These packages are '
                       . 'available on your distribution\'s installation CD.';

#
# Global variables
#
my $gRegistryDir;
my $gStateDir;
my $gInstallerMainDB;
my $gConfFlag;
my %gSystem;
my %gHelper;
# List of all ethernet adapters on the system
my @gAllEthIf;
# List of ethernet adapters that have not been bridged
my @gAvailEthIf;
# By convention, vmnet1 is the virtual ethernet interface connected to the
# private virtual network that Samba uses.  We are also reserving vmnet0
# for bridged networks.  These are reserved vmnets.
my $gDefBridged = '0';
my $gDefHostOnly = '1';
my $gDefNat = '8';
# Reserved vmnets
my @gReservedVmnet = ($gDefBridged, $gDefHostOnly, $gDefNat);
# Constant defined as the smallest vmnet that is allowed
my $gMinVmnet = '0';
# Linux doesn't allow more than 7 characters in the names of network
# interfaces. We prefix host only interfaces with 'vmnet' leaving us only 2
# characters.
# Constant defined as the largest vmnet that is allowed
my $gMaxVmnet = '99';
# Constant defines as the number of vmnets to be pre-created
my $gNumVmnet = 10;
my $gFirstModuleBuild;
my $gDefaultAuthdPort = 902;

# BEGINNING OF THE SECOND LIBRARY FUNCTIONS
# Global variables
my %gDBAnswer;
my %gDBFile;
my %gDBDir;
my $cBackupExtension = '.BeforeVMwareToolsInstall';
my $cRestorePrefix = 'RESTORE_';
my $cRestoreBackupSuffix = '_BAK';
my $cRestoreBackList = 'RESTORE_BACK_LIST';
my $cSwitchedToHost = 'SWITCHED_TO_HOST';
my $cXModulesDir = '/usr/X11R6/lib/modules';
my $cX64ModulesDir = '/usr/X11R6/lib64/modules';
my $gXMouseDriverFile = '';
my $gXVideoDriverFile = '';
my $gIs64BitX = 0;

# Load the installer database
sub db_load {
  undef %gDBAnswer;
  undef %gDBFile;
  undef %gDBDir;

  if (not open(INSTALLDB, '<' . $gInstallerMainDB)) {
    error('Unable to open the installer database ' . $gInstallerMainDB
          . ' in read-mode.' . "\n\n");
  }
  while (<INSTALLDB>) {
    chomp;
    if (/^answer (\S+) (.+)$/) {
      $gDBAnswer{$1} = $2;
    } elsif (/^answer (\S+)/) {
      $gDBAnswer{$1} = '';
    } elsif (/^remove_answer (\S+)/) {
      delete $gDBAnswer{$1};
    } elsif (/^file (.+) (\d+)$/) {
      $gDBFile{$1} = $2;
    } elsif (/^file (.+)$/) {
      $gDBFile{$1} = 0;
    } elsif (/^remove_file (.+)$/) {
      delete $gDBFile{$1};
    } elsif (/^directory (.+)$/) {
      $gDBDir{$1} = '';
    } elsif (/^remove_directory (.+)$/) {
      delete $gDBDir{$1};
    }
  }
  close(INSTALLDB);
}

# Open the database on disk in append mode
sub db_append {
  if (not open(INSTALLDB, '>>' . $gInstallerMainDB)) {
    error('Unable to open the installer database ' . $gInstallerMainDB
          . ' in append-mode.' . "\n\n");
  }
  # Force a flush after every write operation.
  # See 'Programming Perl', p. 110
  select((select(INSTALLDB), $| = 1)[0]);
}

# Add a file to the tar installer database
# flags:
#  0x1 write time stamp
sub db_add_file {
  my $file = shift;
  my $flags = shift;

  if ($flags & 0x1) {
    my @statbuf;

    @statbuf = stat($file);
    if (not (defined($statbuf[9]))) {
      error('Unable to get the last modification timestamp of the destination '
            . 'file ' . $file . '.' . "\n\n");
    }

    $gDBFile{$file} = $statbuf[9];
    print INSTALLDB 'file ' . $file . ' ' . $statbuf[9] . "\n";
  } else {
    $gDBFile{$file} = 0;
    print INSTALLDB 'file ' . $file . "\n";
  }
}

# Remove a file from the tar installer database
sub db_remove_file {
  my $file = shift;

  print INSTALLDB 'remove_file ' . $file . "\n";
  delete $gDBFile{$file};
}

# Remove a directory from the tar installer database
sub db_remove_dir {
  my $dir = shift;

  print INSTALLDB 'remove_directory ' . $dir . "\n";
  delete $gDBDir{$dir};
}

# Determine if a file belongs to the tar installer database
sub db_file_in {
  my $file = shift;

  return defined($gDBFile{$file});
}

# Determine if a directory belongs to the tar installer database
sub db_dir_in {
  my $dir = shift;

  return defined($gDBDir{$dir});
}

# Return the timestamp of an installed file
sub db_file_ts {
  my $file = shift;

  return $gDBFile{$file};
}

# Add a directory to the tar installer database
sub db_add_dir {
  my $dir = shift;

  $gDBDir{$dir} = '';
  print INSTALLDB 'directory ' . $dir . "\n";
}

# Remove an answer from the tar installer database
sub db_remove_answer {
  my $id = shift;

  if (defined($gDBAnswer{$id})) {
    print INSTALLDB 'remove_answer ' . $id . "\n";
    delete $gDBAnswer{$id};
  }
}

# Add an answer to the tar installer database
sub db_add_answer {
  my $id = shift;
  my $value = shift;

  db_remove_answer($id);
  $gDBAnswer{$id} = $value;
  print INSTALLDB 'answer ' . $id . ' ' . $value . "\n";
}

# Retrieve an answer that must be present in the database
sub db_get_answer {
  my $id = shift;

  if (not defined($gDBAnswer{$id})) {
    error('Unable to find the answer ' . $id . ' in the installer database ('
          . $gInstallerMainDB . ').  You may want to re-install '
          . vmware_product_name() . ".\n\n");
  }

  return $gDBAnswer{$id};
}


# Retrieves an answer if it exists in the database, else returns undef;
sub db_get_answer_if_exists {
  my $id = shift;
  if (not defined($gDBAnswer{$id})) {
    return undef;
  }
  if ($gDBAnswer{$id} eq '') {
    return undef;
  }
  return $gDBAnswer{$id};
}

# Save the tar installer database
sub db_save {
  close(INSTALLDB);
}
# END OF THE SECOND LIBRARY FUNCTIONS

# BEGINNING OF THE LIBRARY FUNCTIONS
# Constants
my $cTerminalLineSize = 79;

# Global variables
my %gOption;
my %gAnswerSize;
my %gCheckAnswerFct;

# Tell if the user is the super user
sub is_root {
  return $> == 0;
}

# Wordwrap system: append some content to the output
sub append_output {
  my $output = shift;
  my $pos = shift;
  my $append = shift;

  $output .= $append;
  $pos += length($append);
  if ($pos >= $cTerminalLineSize) {
    $output .= "\n";
    $pos = 0;
  }

  return ($output, $pos);
}

# Wordwrap system: deal with the next character
sub wrap_one_char {
  my $output = shift;
  my $pos = shift;
  my $word = shift;
  my $char = shift;
  my $reserved = shift;
  my $length;

  if (not (($char eq "\n") || ($char eq ' ') || ($char eq ''))) {
    $word .= $char;

    return ($output, $pos, $word);
  }

  # We found a separator.  Process the last word

  $length = length($word) + $reserved;
  if (($pos + $length) > $cTerminalLineSize) {
    # The last word doesn't fit in the end of the line. Break the line before
    # it
    $output .= "\n";
    $pos = 0;
  }
  ($output, $pos) = append_output($output, $pos, $word);
  $word = '';

  if ($char eq "\n") {
    $output .= "\n";
    $pos = 0;
  } elsif ($char eq ' ') {
    if ($pos) {
      ($output, $pos) = append_output($output, $pos, ' ');
    }
  }

  return ($output, $pos, $word);
}

# Wordwrap system: word-wrap a string plus some reserved trailing space
sub wrap {
  my $input = shift;
  my $reserved = shift;
  my $output;
  my $pos;
  my $word;
  my $i;

  $output = '';
  $pos = 0;
  $word = '';
  for ($i = 0; $i < length($input); $i++) {
    ($output, $pos, $word) = wrap_one_char($output, $pos, $word,
                                           substr($input, $i, 1), 0);
  }
  # Use an artifical last '' separator to process the last word
  ($output, $pos, $word) = wrap_one_char($output, $pos, $word, '', $reserved);

  return $output;
}

# Print an error message and exit
sub error {
  my $msg = shift;

  print STDERR wrap($msg . 'Execution aborted.' . "\n\n", 0);
  exit 1;
}

# Convert a string to its equivalent shell representation
sub shell_string {
  my $single_quoted = shift;

  $single_quoted =~ s/'/'"'"'/g;
  # This comment is a fix for emacs's broken syntax-highlighting code --hpreg
  return '\'' . $single_quoted . '\'';
}

# Contrary to a popular belief, 'which' is not always a shell builtin command.
# So we cannot trust it to determine the location of other binaries.
# Moreover, SuSE 6.1's 'which' is unable to handle program names beginning with
# a '/'...
#
# Return value is the complete path if found, or '' if not found
sub internal_which {
  my $bin = shift;

  if (substr($bin, 0, 1) eq '/') {
    # Absolute name
    if ((-f $bin) && (-x $bin)) {
      return $bin;
    }
  } else {
    # Relative name
    my @paths;
    my $path;

    if (index($bin, '/') == -1) {
      # There is no other '/' in the name
      @paths = split(':', $ENV{'PATH'});
      foreach $path (@paths) {
         my $fullbin;

         $fullbin = $path . '/' . $bin;
         if ((-f $fullbin) && (-x $fullbin)) {
               return $fullbin;
         }
      }
    }
  }

  return '';
}

# Remove leading and trailing whitespaces
sub remove_whitespaces {
  my $string = shift;

  $string =~ s/^\s*//;
  $string =~ s/\s*$//;
  return $string;
}

# Ask a question to the user and propose an optional default value
# Use this when you don't care about the validity of the answer
sub query {
    my $message = shift;
    my $defaultreply = shift;
    my $reserved = shift;
    my $reply;

    # Reserve some room for the reply
    print wrap($message . (($defaultreply eq '')
                            ? ''
                            : (' [' . $defaultreply . ']')),
               1 + $reserved);
    # This is what the 1 is for
    print ' ';

    if ($gOption{'default'} == 1) {
      # Simulate the enter key
      print "\n";
      $reply = '';
    } else {
      $reply = <STDIN>;
      $reply = '' unless defined($reply);
      chomp($reply);
    }

    print "\n";
    $reply = remove_whitespaces($reply);
    if ($reply eq '') {
      $reply = $defaultreply;
    }
    return $reply;
}

# Check the validity of an answer whose type is yesno
# Return a clean answer if valid, or ''
sub check_answer_binpath {
  my $answer = shift;
  my $source = shift;

  if (not (internal_which($answer) eq '')) {
    return $answer;
  }

  if ($source eq 'user') {
    print wrap('The answer "' . $answer . '" is invalid.  It must be the '
               . 'complete name of a binary file.' . "\n\n", 0);
  }
  return '';
}
$gAnswerSize{'binpath'} = 20;
$gCheckAnswerFct{'binpath'} = \&check_answer_binpath;

# Prompts the user if a binary is not found
# Return value is:
#  '': the binary has not been found
#  the binary name if it has been found
sub DoesBinaryExist_Prompt {
  my $bin = shift;
  my $answer;
  my $prefix = 'BIN_';

  $answer = check_answer_binpath($bin, 'default');
  if (not ($answer eq '')) {
    return $answer;
  } else {
    if (defined db_get_answer_if_exists($prefix . $bin)) {
      return db_get_answer($prefix . $bin);
    }
  }

  if (get_answer('Setup is unable to find the "' . $bin . '" program on your '
                 . 'machine.  Please make sure it is installed.  Do you want '
                 . 'to specify the location of this program by hand?', 'yesno',
                 'yes') eq 'no') {
    return '';
  }

  $answer = get_answer('What is the location of the "' . $bin . '" program on '
		       . 'your machine?', 'binpath', '');
  if (!defined db_get_answer_if_exists($prefix . $bin)) {
    db_add_answer($prefix . $bin, $answer);
  }
  return $answer;
}

# Execute the command passed as an argument
# _without_ interpolating variables (Perl does it by default)
sub direct_command {
  return `$_[0]`;
}

# chmod() that reports errors
sub safe_chmod {
  my $mode = shift;
  my $file = shift;

  if (chmod($mode, $file) != 1) {
    error('Unable to change the access rights of the file ' . $file . '.'
          . "\n\n");
  }
}

# system chmod() that reports errors
# The $mode parameter must be a string the chmod utility will understand.
sub sys_chmod {
  my $mode = shift;
  my $file = shift;

  if ( system( shell_string($gHelper{'chmod'}) . " $mode $file" ) != 0) {
    error('Unable to change the access rights of the file ' . $file . '.'
          . "\n\n");
  }
}

# chown() that reports errors
sub safe_chown {
  my $uid = shift;
  my $gid = shift;
  my $file = shift;

  if (chown($uid, $gid, $file) != 1) {
    error('Unable to change the owner of the file ' . $file . '.'
          . "\n\n");
  }
}

# Emulate a simplified ls program for directories
sub internal_ls {
  my $dir = shift;
  my @fn;

  opendir(LS, $dir);
  @fn = grep(!/^\.\.?$/, readdir(LS));
  closedir(LS);

  return @fn;
}

# Install a file permission
sub install_permission {
  my $src = shift;
  my $dst = shift;
  my @statbuf;

  @statbuf = stat($src);
  if (not (defined($statbuf[2]))) {
    error('Unable to get the access rights of source file "' . $src . '".'
          . "\n\n");
  }
  safe_chmod($statbuf[2] & 07777, $dst);
}

# Emulate a simplified sed program
# Return 1 if success, 0 if failure
# XXX as a side effect, if the string being replaced is '', remove
# the entire line.  Remove this, once we have better "block handling" of
# our config data in config files.
sub internal_sed {
  my $src = shift;
  my $dst = shift;
  my $append = shift;
  my $patchRef = shift;
  my @patchKeys;

  if (not open(SRC, '<' . $src)) {
    return 0;
  }
  if (not open(DST, (($append == 1) ? '>>' : '>') . $dst)) {
    return 0;
  }

  @patchKeys = keys(%$patchRef);
  if ($#patchKeys == -1) {
    while (defined($_ = <SRC>)) {
      print DST $_;
    }
  } else {
    while (defined($_ = <SRC>)) {
      my $patchKey;
      my $del = 0;

      foreach $patchKey (@patchKeys) {
        if (s/$patchKey/$$patchRef{$patchKey}/g) {
          if ($_ eq "\n") {
            $del = 1;
          }
        }
      }
      if ($del) {
        next;
      }
      print DST $_;
    }
  }

  close(SRC);
  close(DST);
  return 1;
}

# Check if a file name exists
sub file_name_exist {
  my $file = shift;

  # Note: We must test for -l before, because if an existing symlink points to
  #       a non-existing file, -e will be false
  return ((-l $file) || (-e $file))
}

# Check if a file name already exists and prompt the user
# Return 0 if the file can be written safely, 1 otherwise
sub file_check_exist {
  my $file = shift;

  if (not file_name_exist($file)) {
    return 0;
  }

  # The default must make sure that the product will be correctly installed
  # We give the user the choice so that a sysadmin can perform a normal
  # install on a NFS server and then answer 'no' NFS clients
  return (get_answer('The file ' . $file . ' that this program was about to '
                     . 'install already exists.  Overwrite?', 'yesno', 'yes')
            eq 'yes') ? 0 : 1;
}

# Install one file
# flags are forwarded to db_add_file()
sub install_file {
  my $src = shift;
  my $dst = shift;
  my $patchRef = shift;
  my $flags = shift;

  uninstall_file($dst);
  if (file_check_exist($dst)) {
    return;
  }
  # The file could be a symlink to another location.  Remove it
  unlink($dst);
  if (not internal_sed($src, $dst, 0, $patchRef)) {
    error('Unable to copy the source file ' . $src . ' to the destination '
          . 'file ' . $dst . '.' . "\n\n");
  }
  db_add_file($dst, $flags);
  install_permission($src, $dst);
}

# mkdir() that reports errors
sub safe_mkdir {
  my $file = shift;

  if (mkdir($file, 0000) == 0) {
    error('Unable to create the directory ' . $file . '.' . "\n\n");
  }
}

# Remove trailing slashes in a dir path
sub dir_remove_trailing_slashes {
  my $path = shift;

  for (;;) {
    my $len;
    my $pos;

    $len = length($path);
    if ($len < 2) {
      # Could be '/' or any other character.  Ok.
      return $path;
    }

    $pos = rindex($path, '/');
    if ($pos != $len - 1) {
      # No trailing slash
      return $path;
    }

    # Remove the trailing slash
    $path = substr($path, 0, $len - 1)
  }
}

# Emulate a simplified basename program
sub internal_basename {
  return substr($_[0], rindex($_[0], '/') + 1);
}

# Emulate a simplified dirname program
sub internal_dirname {
  my $path = shift;
  my $pos;

  $path = dir_remove_trailing_slashes($path);

  $pos = rindex($path, '/');
  if ($pos == -1) {
    # No slash
    return '.';
  }

  if ($pos == 0) {
    # The only slash is at the beginning
    return '/';
  }

  return substr($path, 0, $pos);
}

# Create a hierarchy of directories with permission 0755
# flags:
#  0x1 write this directory creation in the installer database
# Return 1 if the directory existed before
sub create_dir {
  my $dir = shift;
  my $flags = shift;

  if (-d $dir) {
    return 1;
  }

  if (index($dir, '/') != -1) {
    create_dir(internal_dirname($dir), $flags);
  }
  safe_mkdir($dir);
  if ($flags & 0x1) {
    db_add_dir($dir);
  }
  safe_chmod(0755, $dir);
  return 0;
}

# Get a valid non-persistent answer to a question
# Use this when the answer shouldn't be stored in the database
sub get_answer {
  my $msg = shift;
  my $type = shift;
  my $default = shift;
  my $answer;

  if (not defined($gAnswerSize{$type})) {
    die 'get_answer(): type ' . $type . ' not implemented :(' . "\n\n";
  }
  for (;;) {
    $answer = check_answer(query($msg, $default, $gAnswerSize{$type}), $type,
                           'user');
    if (not ($answer eq '')) {
      return $answer;
    }
    if ($gOption{'default'} == 1) {
      error('Invalid default answer!' . "\n");
    }
  }
}

# Get a valid persistent answer to a question
# Use this when you want an answer to be stored in the database
sub get_persistent_answer {
  my $msg = shift;
  my $id = shift;
  my $type = shift;
  my $default = shift;
  my $answer;

  if (defined($gDBAnswer{$id})) {
    # There is a previous answer in the database
    $answer = check_answer($gDBAnswer{$id}, $type, 'db');
    if (not ($answer eq '')) {
      # The previous answer is valid.  Make it the default value
      $default = $answer;
    }
  }

  $answer = get_answer($msg, $type, $default);
  db_add_answer($id, $answer);
  return $answer;
}

# Find a suitable backup name and backup a file
sub backup_file {
  my $file = shift;
  my $i;

  for ($i = 0; $i < 100; $i++) {
    if (not file_name_exist($file . '.old.' . $i)) {
      my %patch;

      undef %patch;
      if (internal_sed($file, $file . '.old.' . $i, 0, \%patch)) {
         print wrap('File ' . $file . ' is backed up to ' . $file . '.old.'
                    . $i . '.' . "\n\n", 0);
      } else {
         print STDERR wrap('Unable to backup the file ' . $file . ' to '
                           . $file . '.old.' . $i .'.' . "\n\n", 0);
      }
      return;
    }
  }

  print STDERR wrap('Unable to backup the file ' . $file . '.  You have too '
                    . 'many backups files.  They are files of the form '
                    . $file . '.old.N, where N is a number.  Please delete '
                    . 'some of them.' . "\n\n", 0);
}

# Backup a file in the idea to restore it in the future.
sub backup_file_to_restore {
  my $file = shift;
  my $restoreStr = shift;
  if (file_name_exist($file) &&
      (not file_name_exist($file . $cBackupExtension))) {
    my %p;
    undef %p;
    rename $file, $file . $cBackupExtension;
    db_add_answer($cRestorePrefix . $restoreStr, $file);
    db_add_answer($cRestorePrefix . $restoreStr . $cRestoreBackupSuffix,
                  $file . $cBackupExtension);

    if (defined db_get_answer_if_exists($cRestoreBackList)) {
      my $allRestoreStr;
      $allRestoreStr = db_get_answer($cRestoreBackList);
      db_add_answer($cRestoreBackList,$allRestoreStr . ':' . $restoreStr);
    } else {
      db_add_answer($cRestoreBackList, $restoreStr);
    }
  }
}

# XXX Duplicated in pkg_mgr.pl
# format of the returned hash:
#          - key is the system file
#          - value is the backed up file.
# This function should never know about filenames. Only database
# operations.
sub db_get_files_to_restore {
  my %fileToRestore;
  undef %fileToRestore;

  if (defined db_get_answer_if_exists($cRestoreBackList)) {
    my $restoreStr;
    foreach $restoreStr (split(/:/, db_get_answer($cRestoreBackList))) {
      if (defined db_get_answer_if_exists($cRestorePrefix . $restoreStr)) {
        $fileToRestore{db_get_answer($cRestorePrefix . $restoreStr)} =
          db_get_answer($cRestorePrefix . $restoreStr
                        . $cRestoreBackupSuffix);
      }
    }
  }
  return %fileToRestore;
}

# Uninstall a file previously installed by us
sub uninstall_file {
  my $file = shift;

  if (not db_file_in($file)) {
    # Not installed by this program
    return;
  }

  if (file_name_exist($file)) {
    if (db_file_ts($file)) {
      my @statbuf;

      @statbuf = stat($file);
      if (defined($statbuf[9])) {
        if (db_file_ts($file) != $statbuf[9]) {
          # Modified since this program installed it
          backup_file($file);
        }
      } else {
        print STDERR wrap('Unable to get the last modification timestamp of '
                          . 'the file ' . $file . '.' . "\n\n", 0);
      }
    }

    if (not unlink($file)) {
      error('Unable to remove the file "' . $file . '".' . "\n");
    } else {
      db_remove_file($file);
    }

  } else {
    print wrap('This program previously created the file ' . $file . ', and '
               . 'was about to remove it.  Somebody else apparently did it '
               . 'already.' . "\n\n", 0);
    db_remove_file($file);
  }
}

# Uninstall a directory previously installed by us
sub uninstall_dir {
  my $dir = shift;

  if (not db_dir_in($dir)) {
    # Not installed by this program
    return;
  }

  if (-d $dir) {
    if (not rmdir($dir)) {
      print wrap('This program previously created the directory ' . $dir . ', '
                 . 'and was about to remove it. Since there are files in that '
                 . 'directory that this program did not create, it will not be '
                 . 'removed.' . "\n\n", 0);
      if (   defined($ENV{'VMWARE_DEBUG'})
          && ($ENV{'VMWARE_DEBUG'} eq 'yes')) {
        system('ls -AlR ' . shell_string($dir));
      }
    }
  } else {
    print wrap('This program previously created the directory ' . $dir
               . ', and was about to remove it. Somebody else apparently did '
               . 'it already.' . "\n\n", 0);
  }

  db_remove_dir($dir);
}

# Install one directory (recursively)
sub install_dir {
  my $src_dir = shift;
  my $dst_dir = shift;
  my $patchRef = shift;
  my $file;

  if (create_dir($dst_dir, 0x1)) {
    my @statbuf;

    @statbuf = stat($dst_dir);
    if (not (defined($statbuf[2]))) {
      error('Unable to get the access rights of destination directory "' . $dst_dir . '".' . "\n\n");
    }

    # Was bug 15880 --hpreg
    if (   ($statbuf[2] & 0555) != 0555
        && get_answer('Current access permissions on directory "' . $dst_dir
                      . '" will prevent some users from using '
                      . vmware_product_name()
                      . '. Do you want to set those permissions properly?',
                      'yesno', 'yes') eq 'yes') {
      safe_chmod(($statbuf[2] & 07777) | 0555, $dst_dir);
    }
  } else {
    install_permission($src_dir, $dst_dir);
  }
  foreach $file (internal_ls($src_dir)) {
    my $src_loc = $src_dir . '/' . $file;
    my $dst_loc = $dst_dir . '/' . $file;

    if (-l $src_loc) {
      install_symlink(readlink($src_loc), $dst_loc);
    } elsif (-d $src_loc) {
      install_dir($src_loc, $dst_loc, $patchRef);
    } else {
      install_file($src_loc, $dst_loc, $patchRef, 0x1);
    }
  }
}

# Uninstall files and directories beginning with a given prefix
sub uninstall_prefix {
  my $prefix = shift;
  my $prefix_len;
  my $file;
  my $dir;

  $prefix_len = length($prefix);

  # Remove all files beginning with $prefix
  foreach $file (keys %gDBFile) {
    if (substr($file, 0, $prefix_len) eq $prefix) {
      uninstall_file($file);
    }
  }

  # Remove all directories beginning with $prefix
  # We sort them by decreasing order of their length, to ensure that we will
  # remove the inner ones before the outer ones
  foreach $dir (sort {length($b) <=> length($a)} keys %gDBDir) {
    if (substr($dir, 0, $prefix_len) eq $prefix) {
      uninstall_dir($dir);
    }
  }
}

# Return the version of VMware
sub vmware_version {
  my $buildNr;

  $buildNr = '1.0.4 build-56528';
  return remove_whitespaces($buildNr);
}

# Return product name and version
sub vmware_longname {
   my $name = vmware_product_name() . ' ' . vmware_version();

   if (not (vmware_product() eq 'server')) {
      $name .= ' for ' . $gSystem{'system'};
   }

   return $name;
}

# Check the validity of an answer whose type is yesno
# Return a clean answer if valid, or ''
sub check_answer_yesno {
  my $answer = shift;
  my $source = shift;

  if (lc($answer) =~ /^y(es)?$/) {
    return 'yes';
  }

  if (lc($answer) =~ /^n(o)?$/) {
    return 'no';
  }

  if ($source eq 'user') {
    print wrap('The answer "' . $answer . '" is invalid.  It must be one of '
               . '"y" or "n".' . "\n\n", 0);
  }
  return '';
}
$gAnswerSize{'yesno'} = 3;
$gCheckAnswerFct{'yesno'} = \&check_answer_yesno;

# Check the validity of an answer based on its type
# Return a clean answer if valid, or ''
sub check_answer {
  my $answer = shift;
  my $type = shift;
  my $source = shift;

  if (not defined($gCheckAnswerFct{$type})) {
    die 'check_answer(): type ' . $type . ' not implemented :(' . "\n\n";
  }
  return &{$gCheckAnswerFct{$type}}($answer, $source);
}
# END OF THE LIBRARY FUNCTIONS

# BEGINNING_OF_TMPDIR_DOT_PL
#!/usr/bin/perl

use strict;

# Create a temporary directory
#
# They are a lot of small utility programs to create temporary files in a
# secure way, but none of them is standard. So I wrote this --hpreg
sub make_tmp_dir {
  my $prefix = shift;
  my $tmp;
  my $serial;
  my $loop;

  $tmp = defined($ENV{'TMPDIR'}) ? $ENV{'TMPDIR'} : '/tmp';

  # Don't overwrite existing user data
  # -> Create a directory with a name that didn't exist before
  #
  # This may never succeed (if we are racing with a malicious process), but at
  # least it is secure
  $serial = 0;
  for (;;) {
    # Check the validity of the temporary directory. We do this in the loop
    # because it can change over time
    if (not (-d $tmp)) {
      error('"' . $tmp . '" is not a directory.' . "\n\n");
    }
    if (not ((-w $tmp) && (-x $tmp))) {
      error('"' . $tmp . '" should be writable and executable.' . "\n\n");
    }

    # Be secure
    # -> Don't give write access to other users (so that they can not use this
    # directory to launch a symlink attack)
    if (mkdir($tmp . '/' . $prefix . $serial, 0755)) {
      last;
    }

    $serial++;
    if ($serial % 200 == 0) {
      print STDERR 'Warning: The "' . $tmp . '" directory may be under attack.' . "\n\n";
    }
  }

  return $tmp . '/' . $prefix . $serial;
}

# END_OF_TMPDIR_DOT_PL


# Append a clearly delimited block to an unstructured text file --hpreg
# Result:
#  1 on success
#  -1 on failure
sub block_append {
   my $file = shift;
   my $begin = shift;
   my $block = shift;
   my $end = shift;

   if (not open(BLOCK, '>>' . $file)) {
      return -1;
   }

   print BLOCK $begin . $block . $end;

   if (not close(BLOCK)) {
      return -1;
   }

   return 1;
}


# Test if specified file contains line matching regular expression
# Result:
#  undef on failure
#  first matching line on success
sub block_match {
   my $file = shift;
   my $block = shift;
   my $line = undef;

   if (open(BLOCK, '<' . $file)) {
      while (defined($line = <BLOCK>)) {
         chomp $line;
         last if ($line =~ /$block/);
      }
      close(BLOCK);
   }
   return defined($line);
}


# Remove all clearly delimited blocks from an unstructured text file --hpreg
# Result:
#  >= 0 number of blocks removed on success
#  -1 on failure
sub block_remove {
   my $src = shift;
   my $dst = shift;
   my $begin = shift;
   my $end = shift;
   my $count;
   my $state;

   if (not open(SRC, '<' . $src)) {
      return -1;
   }

   if (not open(DST, '>' . $dst)) {
      close(SRC);
      return -1;
   }

   $count = 0;
   $state = 'outside';
   while (<SRC>) {
      if      ($state eq 'outside') {
         if ($_ eq $begin) {
            $state = 'inside';
            $count++;
         } else {
            print DST $_;
         }
      } elsif ($state eq 'inside') {
         if ($_ eq $end) {
            $state = 'outside';
         }
      }
   }

   if (not close(DST)) {
      close(SRC);
      return -1;
   }

   if (not close(SRC)) {
      return -1;
   }

   return $count;
}


# Set the name of the main /etc/vmware* directory.
sub initialize_globals {

  if (vmware_product() eq 'console') {
    $gRegistryDir = '/etc/vmware-server-console';
  } elsif (vmware_product() eq 'mui') {
    $gRegistryDir = '/etc/vmware-mui';
  } elsif (vmware_product() eq 'tools-for-linux' ||
           vmware_product() eq 'tools-for-freebsd' ||
           vmware_product() eq 'tools-for-solaris') {
    $gRegistryDir = '/etc/vmware-tools';
  } else {
    $gRegistryDir = '/etc/vmware';
  }
  $gStateDir = $gRegistryDir . '/state';
  $gInstallerMainDB = $gRegistryDir . '/locations';
  $gConfFlag = $gRegistryDir . '/not_configured';

  $gOption{'default'} = 0;
  $gOption{'compile'} = 0;
  $gOption{'prebuilt'} = 0;
  $gOption{'try-modules'} = 0;
  $gOption{'tools-switch'} = 0;
  $gOption{'overwriteSVGA'} = 0;

}


# Set up the location of external helpers
sub initialize_external_helpers {
  my $program;
  my @programList;

  if (not defined($gHelper{'more'})) {
    $gHelper{'more'} = '';
    if (defined($ENV{'PAGER'})) {
      my @tokens;

      # The environment variable sometimes contains the pager name _followed by
      # a few command line options_.
      #
      # Isolate the program name (we are certain it does not contain a
      # whitespace) before dealing with it.
      @tokens = split(' ', $ENV{'PAGER'});
      $tokens[0] = DoesBinaryExist_Prompt($tokens[0]);
      if (not ($tokens[0] eq '')) {
        # This is _already_ a shell string
        $gHelper{'more'} = join(' ', @tokens);
      }
    }
    if ($gHelper{'more'} eq '') {
      $gHelper{'more'} = DoesBinaryExist_Prompt('more');
      if ($gHelper{'more'} eq '') {
        error('Unable to continue.' . "\n\n");
      }
      # Save it as a shell string
      $gHelper{'more'} = shell_string($gHelper{'more'});
    }
  }

  if (vmware_product() eq 'tools-for-freebsd') {
    @programList = ('cp', 'uname', 'grep', 'ldd', 'mknod', 'kldload',
                    'kldunload', 'rm', 'chmod');
  } elsif (vmware_product() eq 'tools-for-solaris') {
    # Note that svcprop(1) is added for Solaris 10 and later after it is
    # guaranteed that uname(1) has been found
    @programList = ('cp', 'uname', 'grep', 'ldd', 'mknod', 'modload',
                    'modunload', 'add_drv', 'rem_drv', 'update_drv',
                    'rm', 'isainfo', 'ifconfig', 'cat', 'mv', 'sed',
                    'cut', 'chmod');
  } else {
    @programList = ('cp', 'uname', 'grep', 'ldd', 'mknod', 'insmod',
                    'lsmod', 'modprobe', 'rmmod', 'ifconfig', 'rm', 'chmod');
  }

  foreach $program (@programList) {
    if (not defined($gHelper{$program})) {
      $gHelper{$program} = DoesBinaryExist_Prompt($program);
      if ($gHelper{$program} eq '') {
        error('Unable to continue.' . "\n\n");
      }
    }
  }

  if (vmware_product() eq 'tools-for-solaris' &&
      solaris_10_or_greater() eq 'yes') {
    $gHelper{'svcprop'} = DoesBinaryExist_Prompt('svcprop');
    if ($gHelper{'svcprop'} eq '') {
      error('Unable to continue.' . "\n\n");
    }
  }
  $gHelper{'insserv'} = internal_which('insserv');
  $gHelper{'chkconfig'} = internal_which('/sbin/chkconfig');
  if (vmware_product() eq 'server' &&
      $gHelper{'chkconfig'} eq '') {
         error('No initscript installer found.' . "\n\n");
  }
}


# Check the validity of an answer whose type is dirpath
# Return a clean answer if valid, or ''
sub check_answer_dirpath {
    my $answer = shift;
    my $source = shift;

    $answer = dir_remove_trailing_slashes($answer);

    if (substr($answer, 0, 1) ne '/') {
	print wrap('The path "' . $answer . '" is a relative path. Please enter '
		   . 'an absolute path.' . "\n\n", 0);
	return '';
    }

    if (-d $answer) {
	# The path is an existing directory
	return $answer;
    }

    # The path is not a directory
    if (file_name_exist($answer)) {
	if ($source eq 'user') {
	    print wrap('The path "' . $answer . '" exists, but is not a directory.'
		       . "\n\n", 0);
	}
	return '';
    }

    # The path does not exist
    if ($source eq 'user') {
	return (get_answer('The path "' . $answer . '" does not exist currently. '
			   . 'This program is going to create it, including needed '
			   . 'parent directories. Is this what you want?',
			   'yesno', 'yes') eq 'yes') ? $answer : '';
    } else {
	return $answer;
    }
}
$gAnswerSize{'dirpath'} = 20;
$gCheckAnswerFct{'dirpath'} = \&check_answer_dirpath;


# Check the validity of an answer whose type is dirpath_existing
# Return an existing directory if valid, or ''
sub check_answer_dirpath_existing {
    my $answer = shift;
    my $source = shift;

    $answer = dir_remove_trailing_slashes($answer);

    if (substr($answer, 0, 1) ne '/') {
	print wrap('The path "' . $answer . '" is a relative path. Please enter '
		   . 'an absolute path.' . "\n\n", 0);
	return '';
    }

    if (-d $answer) {
	# The path is an existing directory
	return $answer;
    }

    # The path is not a directory
    if (file_name_exist($answer) && ($source eq 'user')) {
      print wrap('The path "' . $answer . '" exists, but is not a directory.'
		 . "\n\n", 0);
    } else {
      # The path does not exist
      print wrap('The path "' . $answer . '" does not exist.' . "\n\n", 0);
    }
    return '';
}
$gAnswerSize{'dirpath_existing'} = 20;
$gCheckAnswerFct{'dirpath_existing'} = \&check_answer_dirpath_existing;


# Check the validity of an answer whose type is headerdir
# Return a clean answer if valid, or ''
sub check_answer_headerdir {
  my $answer = shift;
  my $source = shift;
  my $pattern = '@@VMWARE@@';
  my $header_version_uts;
  my $header_smp;
  my $uts_headers;

  $answer = dir_remove_trailing_slashes($answer);

  if (not (-d $answer)) {
    if ($source eq 'user') {
      print wrap('The path "' . $answer . '" is not an existing directory.'
                 . "\n\n", 0);
    }
    return '';
  }

  if ($answer =~ m|^/usr/include(/.*)?$|) { #/# Broken colorizer.
    if ($source eq 'user') {
      if (get_answer('The header files in /usr/include are generally for C '
                     . 'libraries, not for the running kernel. If you do not '
                     . 'have kernel header files in your /usr/src directory, '
                     . 'you probably do not have the kernel-source package '
                     . 'installed. Are you sure that /usr/include contains '
                     . 'the header files associated with your running kernel?',
                     'yesno', 'no') eq 'no') {
        return '';
      }
    }
  }

  if (not (-d $answer . '/linux')) {
    if ($source eq 'user') {
      print wrap('The path "' . $answer . '" is an existing directory, but it '
                 . 'does not contain a "linux" subdirectory as expected.'
                 . "\n\n", 0);
    }
    return '';
  }

  #
  # Check that the running kernel matches the set of header files
  #

  if (not (-r $answer . '/linux/version.h')) {
    if ($source eq 'user') {
      print wrap('The path "' . $answer . '" is a kernel header file '
                 . 'directory, but it does not contain the file '
                 . '"linux/version.h" as expected.  This can happen if the '
                 . 'kernel has never been built, or if you have invoked the '
                 . '"make mrproper" command in your kernel directory.  In any '
                 . 'case, you may want to rebuild your kernel.' . "\n\n", 0);
    }
    return '';
  }

  #
  # Kernels before 2.6.18 declare UTS_RELEASE in version.h.  Newer kernels
  # use utsrelease.h.  We include both just in case somebody moves UTS_RELEASE
  # back while leaving utsrelease.h file in place.
  #
  $uts_headers = "#include <linux/version.h>\n";
  if (-e $answer . '/linux/utsrelease.h') {
    $uts_headers .= "#include <linux/utsrelease.h>\n";
  }
  $header_version_uts = direct_command(
    shell_string($gHelper{'echo'}) . ' '
    . shell_string($uts_headers . $pattern
                   . ' UTS_RELEASE') . ' | ' . shell_string($gHelper{'gcc'})
    . ' ' . shell_string('-I' . $answer) . ' -E - | '
    . shell_string($gHelper{'grep'}) . ' ' . shell_string($pattern));
  chomp($header_version_uts);
  $header_version_uts =~ s/^$pattern \"([^\"]*)\".*$/$1/;
  if (not ($header_version_uts eq $gSystem{'uts_release'})) {
    if ($source eq 'user') {
      print wrap('The directory of kernel headers (version '
                 . $header_version_uts . ') does not match your running '
                 . 'kernel (version ' . $gSystem{'uts_release'} . ').  Even '
                 . 'if the module were to compile successfully, it would not '
                 . 'load into the running kernel.' . "\n\n", 0);
    }
    return '';
  }

  if (not (-r $answer . '/linux/autoconf.h')) {
    if ($source eq 'user') {
      print wrap('The path "' . $answer . '" is a kernel header file '
                 . 'directory, but it does not contain the file '
                 . '"linux/autoconf.h" as expected.  This can happen if the '
                 . 'kernel has never been built, or if you have invoked the '
                 . '"make mrproper" command in your kernel directory.  In any '
                 . 'case, you may want to rebuild your kernel.' . "\n\n", 0);
    }
    return '';
  }
  $header_smp = direct_command(shell_string($gHelper{'grep'}) . ' CONFIG_SMP '
                               . shell_string($answer . '/linux/autoconf.h'));
  if (not ($header_smp eq '')) {
    # linux/autoconf.h contains the up/smp information
    $header_smp = direct_command(
      shell_string($gHelper{'echo'}) . ' '
      . shell_string('#include <linux/autoconf.h>' . "\n" . $pattern
                     . ' CONFIG_SMP') . ' | ' . shell_string($gHelper{'gcc'})
      . ' ' . shell_string('-I' . $answer) . ' -E - | '
      . shell_string($gHelper{'grep'}) . ' ' . shell_string($pattern));
    chomp($header_smp);
    $header_smp =~ s/^$pattern (\S+).*$/$1/;
    $header_smp = ($header_smp eq '1') ? 'yes' : 'no';
    if (not (lc($header_smp) eq lc($gSystem{'smp'}))) {
      if ($source eq 'user') {
        print wrap('The kernel defined by this directory of header files is '
                   . (($header_smp eq 'yes') ? 'multiprocessor'
                                             : 'uniprocessor') . ', while '
                   . 'your running kernel is '
                   . (($gSystem{'smp'} eq 'yes') ? 'multiprocessor'
                                                 : 'uniprocessor') . '.'
                   . "\n\n", 0);
      }
      return '';
    }
  }

  #
  # For kernels before 2.6.0 require asm and net subdirectories.  And verify
  # that PAGE_OFFSET for running kernel matches one specified in kernel
  # headers.  We use our Makefiles to build kernel modules on these kernels,
  # so we know that asm and net directories must be here for successful build,
  # and PAGE_OFFSET must match.
  #
  # For kernel 2.6.0 and above require ../Makefile and ../.config presence.
  # Although they could be theoretically missing, they are present on all
  # currently existing systems.  And check for ../.config presence
  # rules out /usr/src/linux/include eliminates false positive we
  # currently hit on SuSE 9.x systems.  And do not verify PAGE_OFFSET value
  # at all, asm/page.h needs special processing on 2.6.15+ kernels.
  #
  if ($header_version_uts =~ /^2\.[0-5]\./) {
    if (   (not (-d $answer . '/asm'))
        || (not (-d $answer . '/net'))) {
      if ($source eq 'user') {
        print wrap('The path "' . $answer . '" is an existing directory, but it '
                   . 'does not contain subdirectories "asm" and "net" as expected.'
                   . "\n\n", 0);
      }
      return '';
    }
    if (not (-r $answer . '/asm/page.h')) {
      if ($source eq 'user') {
        print wrap('The path "' . $answer . '" is a kernel header file '
                   . 'directory, but it does not contain the file "asm/page.h" '
                   . 'as expected.' . "\n\n", 0);
      }
      return '';
    }
    my $header_page_offset = direct_command(
      shell_string($gHelper{'echo'}) . ' '
      . shell_string('#define __KERNEL__' . "\n" . '#include <asm/page.h>'
                     . "\n" . $pattern . ' __PAGE_OFFSET') . ' | '
      . shell_string($gHelper{'gcc'}) . ' ' . shell_string('-I' . $answer)
      . ' -E - | ' . shell_string($gHelper{'grep'}) . ' '
      . shell_string($pattern));
    chomp($header_page_offset);
    # Ignore PAGE_OFFSET if we cannot parse it.
    if ($header_page_offset =~ /^$pattern \(?0x([0-9a-fA-F]{8,})/) {
      # We found a valid page offset
      $header_page_offset = $1;
      if (defined($gSystem{'page_offset'}) and
          not (lc($header_page_offset) eq lc($gSystem{'page_offset'}))) {
        if ($source eq 'user') {
          print wrap('The kernel defined by this directory of header files does '
                     . 'not have the same address space size as your running '
                     . 'kernel.' . "\n\n", 0);
        }
        return '';
      }
    }
  } else {
    if (not (-r $answer . '/../Makefile')) {
      if ($source eq 'user') {
        print wrap('The path "' . $answer . '" is a kernel header file '
                   . 'directory, but it is not part of kernel source tree.'
                   . "\n\n", 0);
      }
      return '';
    }
    if (not (-r $answer . '/../.config')) {
      if ($source eq 'user') {
        print wrap('The path "' . $answer . '" is a kernel header file '
                   . 'directory, but it is not configured yet.'
                   . "\n\n", 0);
      }
      return '';
    }
  }
  return $answer;
}
$gAnswerSize{'headerdir'} = 20;
$gCheckAnswerFct{'headerdir'} = \&check_answer_headerdir;

# Check the validity of an answer whose type is ip
# Return a clean answer if valid, or ''
sub check_answer_ip {
  my $answer = shift;
  my $source = shift;
  my $re;

  # I'm in love with regular expressions --hpreg
  $re = '^([0-9]|[1-9][0-9]|1[0-9][0-9]|2([0-4][0-9]|5[0-5]))'
        . '(\.([0-9]|[1-9][0-9]|1[0-9][0-9]|2([0-4][0-9]|5[0-5]))){3}$';
  # This comment fixes emacs's broken syntax highlighting
  if ($answer =~ /$re/) {
    return $answer;
  }

  if ($source eq 'user') {
    print wrap('The answer "' . $answer . '" is invalid.  It must be of the '
               . 'form a.b.c.d where a, b, c and d are decimal numbers '
               . 'between 0 and 255.' . "\n\n", 0);
  }
  return '';
}
$gAnswerSize{'ip'} = 15;
$gCheckAnswerFct{'ip'} = \&check_answer_ip;

# Check the validity of an answer whose type is serial number
# Return a clean answer if valid, or ''
sub check_answer_serialnum {
  my $answer = shift;
  my $source = shift;
  my $re;

  if ($answer eq '') {
      return ' ';
  }

  $re = '^(([0-9]|[A-Z]){5}-){3}(([0-9]|[A-Z]){5})$';
  # This comment fixes emacs's broken syntax highlighting
  if ($answer =~ /$re/) {
    return $answer;
  }

  if ($source eq 'user') {
    print wrap('The answer "' . $answer . '" is invalid.  It must be of the '
               . 'form XXXXX-XXXXX-XXXXX-XXXXX where X is a digit 0-9 or a '
	       . 'capital letter A-Z' . "\n\n", 0);
  }
  return '';
}
$gAnswerSize{'serialnum'} = 23;
$gCheckAnswerFct{'serialnum'} = \&check_answer_serialnum;

# Check the validity of an answer whose type is editorwizardhelp
# Return a clean answer if valid, or ''
sub check_answer_editorwizardhelp {
  my $answer = shift;
  my $source = shift;

  if (lc($answer) =~ /^e(ditor)?$/) {
    return 'editor';
  }

  if (lc($answer) =~ /^w(izard)?$/) {
    return 'wizard';
  }

  if (lc($answer) =~ /^h(elp)?$/) {
    return 'help';
  }

  if ($source eq 'user') {
    print wrap('The answer "' . $answer . '" is invalid. It must be one of '
               . '"w", "e" or "h".' . "\n\n", 0);
  }
  return '';
}
$gAnswerSize{'editorwizardhelp'} = 6;
$gCheckAnswerFct{'editorwizardhelp'} = \&check_answer_editorwizardhelp;

# Check the validity of an answer whose type is yesnohelp
# Return a clean answer if valid, or ''
sub check_answer_yesnohelp {
  my $answer = shift;
  my $source = shift;

  if (lc($answer) =~ /^y(es)?$/) {
    return 'yes';
  }

  if (lc($answer) =~ /^n(o)?$/) {
    return 'no';
  }

  if (lc($answer) =~ /^h(elp)?$/) {
    return 'help';
  }

  if ($source eq 'user') {
    print wrap('The answer "' . $answer . '" is invalid.  It must be one of '
               . '"y", "n" or "h".' . "\n\n", 0);
  }
  return '';
}
$gAnswerSize{'yesnohelp'} = 4;
$gCheckAnswerFct{'yesnohelp'} = \&check_answer_yesnohelp;

# Check the validity of an answer whose type is vmnet
# Return a clean answer if valid, or ''
sub check_answer_vmnet {
  my $answer = shift;
  my $source = shift;

  if ($answer =~ /^\d+$/) {
    if ($answer >= $gMinVmnet && $answer <= $gMaxVmnet) {
      return $answer;
    }
  }

  if ($source eq 'user') {
    print wrap('The answer "' . $answer . '" is invalid. It must be an '
               . 'integer between ' . $gMinVmnet . ' and ' . $gMaxVmnet . '.'
               . "\n\n", 0);
  }

  return '';
}
$gAnswerSize{'vmnet'} = length("$gMaxVmnet");
$gCheckAnswerFct{'vmnet'} = \&check_answer_vmnet;

# Check the validity of an answer whose type is nettype
# Return a clean answer if valid, or ''
sub check_answer_nettype {
  my $answer = shift;
  my $source = shift;

  if (lc($answer) =~ /^h(ostonly)?$/) {
    return 'hostonly';
  }

  if (lc($answer =~ /^b(ridged)?$/)) {
    return 'bridged';
  }

  if (lc($answer =~ /^n(at)?$/)) {
    return 'nat';
  }

  if (lc($answer =~ /^none$/)) {
    return 'none';
  }

  if ($source eq 'user') {
    print wrap('The answer "' . $answer . '" is invalid. It must be either '
               . '"b", "h", "n", or "none".' . "\n\n", 0);
  }
  return '';
}
$gAnswerSize{'nettype'} = 8;
$gCheckAnswerFct{'nettype'} = \&check_answer_nettype;

# Check the validity of an answer whose type is availethif
# Return a clean answer if valid, or ''
sub check_answer_availethif {
  my $answer = shift;
  my $source = shift;

  if (grep($answer eq $_, @gAvailEthIf)) {
    return $answer;
  }

  if ($source eq 'user') {
    if (grep($answer eq $_, @gAllEthIf)) {
      print wrap('The ethernet device "' . $answer . '" is already configured '
                 . 'as a bridged device.' . "\n\n", 0);
      return '';
    }
    if (get_answer('The ethernet device "' . $answer . '" was not detected on '
                   . 'your system.  Available ethernet devices detected on '
                   . 'your system include ' . join(', ', @gAvailEthIf) . '.  '
                   . 'Are you sure you want to use this device? (yes/no)',
                   'yesno', 'no') eq 'no') {
      return '';
    } else {
      return $answer;
    }
  }
  return '';
}
$gAnswerSize{'availethif'} = 4;
$gCheckAnswerFct{'availethif'} = \&check_answer_availethif;

# check the validity of a user or group name
# return the answer if valid or ''
sub check_answer_usergp {
  my $answer = shift;
  my $source = shift;

  if (($answer=~/^\S+$/) && ($answer=~/^[a-zA-Z]/)) {
    return $answer;
  }

  if ($source eq 'user') {
    print wrap('The answer "' . $answer . '" is invalid. Please enter a valid'
               . ' name of length < 32 and beginning with a letter'
               . "\n\n", 0);
  }

  return '';
}

$gAnswerSize{'usergp'} = 32;
$gCheckAnswerFct{'usergp'} = \&check_answer_usergp;

# check the validity of a timeout value
# return the answer if valid or ''
sub check_answer_timeout {
  my $answer = shift;
  my $source = shift;

  if ($answer=~/^-?\d+$/ && $answer >= -1) {
    return $answer;
  }

  if ($source eq 'user') {
    print wrap('The answer "' . $answer . '" is invalid. Please enter a valid'
               . ' number of minutes in the range -1 to 99999' . "\n\n", 0);
  }

  return '';
}

$gAnswerSize{'timeout'} = 5;
$gCheckAnswerFct{'timeout'} = \&check_answer_timeout;


# Check the validity of an answer whose type is nocheck
# Always returns answer.
sub check_answer_anyethif {
  my $answer = shift;
  my $source = shift;

  return $answer;
}
$gAnswerSize{'anyethif'} = 4;
$gCheckAnswerFct{'anyethif'} = \&check_answer_anyethif;

# Check the validity of an answer whose type is authdport
# Return a clean answer if valid, or ''
sub check_answer_authdport {
  my $answer = shift;
  my $source = shift;

  if ($source eq 'default') {
    if (check_if_port_free($answer) != 1) {
      return '';
    }
  }

  if (($answer =~ /^\d+$/) && ($answer > 0) && ($answer < 65536)) {
    return $answer;
  }

  if ($source eq 'user') {
    print wrap('The answer "' . $answer . '" is invalid. Please enter a valid '
               . 'port number in the range 1 to 65535.' . "\n\n", 0);
  }

  return '';
}
$gAnswerSize{'authdport'} = 5;
$gCheckAnswerFct{'authdport'} = \&check_answer_authdport;

# Check the validity of an answer whose type is number
# Return a clean number if valid, or '0'
# Default value for the 'number' type of answer.
# This $gMaxNumber as well as the $gAnswerSize{'number'} has to be updated
# before calling get_*_answer functions so that wrap() leaves enough room
# for the reply.
my $gMaxNumber = 0;
sub check_answer_number {
  my $answer = shift;
  my $source = shift;

  if (($answer =~ /^\d+$/) && ($answer > 0) && ($answer <= $gMaxNumber)) {
    return $answer;
  }

  if ($source eq 'user') {
    print wrap('The answer "' . $answer . '" is invalid. Please enter a valid '
               . 'number in the range 1 to ' . $gMaxNumber . "\n\n", 0);
  }

  return '';
}
$gAnswerSize{'number'} = length($gMaxNumber);
$gCheckAnswerFct{'number'} = \&check_answer_number;

my %gPortCache;
# Check $cServices file for specified port
# If $cServices cant be read, return -1
# If port not in $cServices return 1
# If port is in $cServices return 0
sub check_port_not_registered {
  my $port = shift;
  if (defined($gPortCache{$port}) && $gPortCache{$port} == 2) {
    return 0;
  }
  if (not open(CONF, $cServices)) {
    return -1;
  }
  while (<CONF>) {
    if (/\b(\d+)\/(tcp)\b/i) {
      $gPortCache{$1} = 2;
    }
  }
  close(CONF);
  if (defined($gPortCache{$port}) && $gPortCache{$port} == 2) {
    return 0;
  }
  return 1;

}


# Check the $cServices file and use /proc/net/tcp to see
# if the port is already in use.
# If we fail to check, return -1
# If port is free, return 1;
# If port is in use, return 0;
sub check_if_port_free {
  my $port = shift;
  if (defined($gPortCache{$port})) {
    return 0;
  }
  # Check /proc/net/tcp and /proc/net/udp
  if (open(TCP, "</proc/net/tcp")) {
    while (<TCP>) {
      if (/^\s*\d+:\s*[0-9a-fA-F]{8}:([0-9a-fA-F]{4})\s*[0-9a-fA-F]{8}:[0-9a-fA-F]{4}\s*([0-9a-fA-F]{2}).*$/) {
        # We'll consider a socket free if it is in TIME_WAIT state
        if ($2 ne "06") {
          $gPortCache{hex($1)} = 1;
        }
      }
    }
    close TCP;
  }
  if (defined($gPortCache{$port})) {
    return 0;
  }
  return check_port_not_registered($port);
}


# Display the end-user license agreement
sub show_EULA {
  if (   (not defined($gDBAnswer{'EULA_AGREED'}))
      || (db_get_answer('EULA_AGREED') eq 'no')) {
    if ($gOption{'default'} == 1) {
       print wrap('You must read and accept the End User License Agreement to '
                  . 'continue.' . "\n\n" . 'To display End User License '
                  . 'Agreement please restart ' . $0 . ' in the '
                  . 'interactive mode, without using `-d\' option.' . "\n\n", 0);
       exit 0;
    }
    query('You must read and accept the End User License Agreement to '
          . 'continue.' . "\n" . 'Press enter to display it.', '', 0);

    # $gHelper{'more'} is already a shell string
    system($gHelper{'more'} . ' ' . shell_string(db_get_answer('DOCDIR')
                                                 . '/EULA'));
    print "\n";

    # Make sure there is no default answer here
    if (get_persistent_answer('Do you accept? (yes/no)', 'EULA_AGREED',
                              'yesno', '') eq 'no') {
      print wrap('Please try again when you are ready to accept.' . "\n\n", 0);
      exit 0;
    }

    print wrap('Thank you.' . "\n\n", 0);
  }
}

# Build a Linux kernel integer version
sub kernel_version_integer {
  my $version = shift;
  my $patchLevel = shift;
  my $subLevel = shift;

  return $version * 65536 + $patchLevel * 256 + $subLevel;
}

# Retrieve distribution information
sub distribution_info {
  my $issue = '/etc/issue';
  my $system;

  # First use the accurate method that are intended to work reliably on recent
  # distributions (if an FHS guy is listening, we really need a generic way to
  # do this)
  if (-e '/etc/debian_version') {
    return 'debian';
  }
  if (-e '/etc/redhat-release') {
    return 'redhat';
  }
  if (-e '/etc/SuSE-release') {
    return 'suse';
  }
  if (-e '/etc/turbolinux-release') {
    return 'turbolinux';
  }
  if (-e '/etc/mandrake-release') {
    return 'mandrake';
  }

  # Then use less accurate methods that should work even on old distributions,
  # if people haven't customized their system too much
  if (-e $issue) {
    if (not (direct_command(shell_string($gHelper{'grep'}) . ' -i '
                            . shell_string('debian') . ' '
                            . shell_string($issue)) eq '')) {
      return 'debian';
    }
    if (not (direct_command(shell_string($gHelper{'grep'}) . ' -i '
                            . shell_string('red *hat') . ' '
                            . shell_string($issue)) eq '')) {
      return 'redhat';
    }
    if (not (direct_command(shell_string($gHelper{'grep'}) . ' -i '
                            . shell_string('suse\|s\.u\.s\.e') . ' '
                            . shell_string($issue)) eq '')) {
      return 'suse';
    }
    if (not (direct_command(shell_string($gHelper{'grep'}) . ' -i '
                            . shell_string('caldera') . ' '
                            . shell_string($issue)) eq '')) {
      return 'caldera';
    }
  }

  return 'unknown';
}

sub vmware_check_vm_app_name {
  return db_get_answer('SBINDIR') . '/vmware-checkvm';
}

sub vmware_vmx_app_name {
  return db_get_answer('LIBDIR') . '/bin/vmware-vmx';
}

sub isFreeBSDLibc6 {
   if (vmware_product() eq 'tools-for-freebsd') {
      if (-f '/lib/libc.so.6') {
         return 1;
      }
   }
   return 0;
}

sub is64BitKernel {
  if (vmware_product() eq 'tools-for-solaris') {
    if (direct_command(shell_string($gHelper{'isainfo'}) . ' -k') =~ /amd64/) {
      return 1;
    } else {
      return 0;
    }
  }

  if (direct_command(shell_string($gHelper{'uname'}) . ' -m') =~ /(x86_64|amd64)/) {
    return 1;
  } else {
    return 0;
  }
}

sub is64BitUserland {
  if (vmware_product() eq 'tools-for-solaris') {
    # Currently always say no since we are only using 32-bit applications.
    return 0;
    # The code below should replace the return above when we have 64-bit builds
    #if (direct_command(shell_string($gHelper{'isainfo'}) . ' -b') =~ /64/) {
    #  return 1;
    #} else {
    #  return 0;
    #}
  }
  if ($Config{archname} =~ /^(x86_64|amd64)-/) {
    return 1;
  } else {
    return 0;
  }
}

# The installer packages up both 32 and 64 bit userlevel binaries, leaving them all
# in LIBDIR. This function links the correct thing in BINDIR and SBINDIR. This
# "installs" vmware-checkvm, vmware-guestd, wrapper script for vmware-toolbox and
# vmware-user.
sub setup32or64Symlinks {
  my $is64BitUserland = is64BitUserland();
  my $libdir = db_get_answer('LIBDIR');
  my $libbindir = $libdir . ($is64BitUserland ? '/bin64' : '/bin32');
  my $libsbindir = $libdir . ($is64BitUserland ? '/sbin64' : '/sbin32');
  my $liblibdir = $libdir . ($is64BitUserland ? '/lib64' : '/lib32');
  my $pamdfile = $libdir . '/configurator/pam.d/vmware-guestd' . ($is64BitUserland ? '-x64' : '');
  my $bindir = db_get_answer('BINDIR');
  my $sbindir = db_get_answer('SBINDIR');

  if (isFreeBSDLibc6()) {
     $libbindir .= '-6';
     $libsbindir .= '-6';
  }
  install_symlink($libsbindir . '/vmware-checkvm',
                  $sbindir . '/vmware-checkvm');
  install_symlink($libsbindir . '/vmware-guestd',
                  $sbindir . '/vmware-guestd');
  install_symlink($libbindir . '/vmware-toolbox',
                  $bindir . '/vmware-toolbox');
  if (vmware_product() eq 'tools-for-linux') {
     install_symlink($libbindir . '/vmware-user-wrapper',
                     $bindir . '/vmware-user');
  }
  if (vmware_product() eq 'tools-for-solaris') {
     install_symlink($libsbindir . '/vmware-memctld',
                     $sbindir . '/vmware-memctld');
  }
  if (vmware_product() eq 'tools-for-linux') {
    install_symlink($pamdfile, '/etc/pam.d/vmware-guestd');
    install_symlink($liblibdir . '/libvmGuestLib.so', $libdir . '/../libvmGuestLib.so');
  }
}

# The installer packages up both the TCL and GTK toolboxes for FreeBSD.  This
# function adds a LIBDIR/vmware-toolbox symlink to the correct version, which
# is then linked to via the setup32or64Symlinks function.
sub setupTclOrGtkSymlinks {
   my $release = `uname -r | cut -f1 -d-`;
   my $libdir = db_get_answer('LIBDIR');
   my $toolbox;

   if ($release < 5.3) {
      $toolbox = 'tcl';
   } else {
      # The GTK toolbox is wrapped with a script that
      # preloads needed libraries
      $toolbox = 'gtk-wrapper';
   }
   foreach my $dir (qw(bin32 bin64 bin32-6 bin64-6)) {
      install_symlink('vmware-toolbox-' . $toolbox,
                      $libdir . '/' . $dir . '/vmware-toolbox');
   }
}


# Open a file binary and read the ELF header. We really only care about the fifth
# byte, EI_CLASS. I pulled the values from /usr/include/elf.h
sub is64BitElf {
  my $file = shift;
  my ($buf, $buf2);
  my $cEI_CLASS = 4;
  my $cELFCLASS64 = 2;
  my $cEI_MAG0 = 0;
  my $cSELFMAG = 4;
  my $cELFMAG = "\x7FELF";

  open(X_BIN, '<' . $file) || return 0;
  seek(X_BIN, $cEI_MAG0, 0) || return 0;
  read(X_BIN, $buf, $cSELFMAG)  || return 0;
  ($buf2) = unpack("a4", $buf);
  if ($buf2 ne $cELFMAG) {
      return 0;
  }

  seek(X_BIN, $cEI_CLASS, 0) || return 0;
  read(X_BIN, $buf, 1)  || return 0;
  ($buf2) = unpack("C", $buf);
  return ($buf2 eq $cELFCLASS64);
}


# Retrieve and check system information
sub system_info {
  my $fullVersion;
  my $version;
  my $patchLevel;
  my $subLevel;
  my $runSystem;

  $gSystem{'system'} = direct_command(shell_string($gHelper{'uname'}) . ' -s');
  chomp($gSystem{'system'});

  if (vmware_product() eq 'tools-for-freebsd') {
     $runSystem = 'FreeBSD';
  } elsif (vmware_product() eq 'tools-for-solaris') {
     $runSystem = 'SunOS';
  } else {
     $runSystem = 'Linux';
  }

  if (not ($gSystem{'system'} eq $runSystem)) {
    error('You are not running ' . $runSystem . '. This version of the product '
          . 'only runs on ' . $runSystem . '.' . "\n\n");
  }

  # Users will expect the output to be "Solaris", despite what uname -s says
  if (vmware_product() eq 'tools-for-solaris') {
    $gSystem{'system'} = 'Solaris';
  }

  if (vmware_product() eq 'server') {
    # Force the answer even if they're running Linux right now.
    $gSystem{'uts_release'} = '@@VMNIXVERSION@@';
  } else {
    $gSystem{'uts_release'} = direct_command(shell_string($gHelper{'uname'})
                                             . ' -r');
    chomp($gSystem{'uts_release'});
  }
  $gSystem{'uts_version'} = direct_command(shell_string($gHelper{'uname'})
                                           . ' -v');
  chomp($gSystem{'uts_version'});

  if ($runSystem eq 'Linux') {

    ($version, $patchLevel, $subLevel) = split(/\./, $gSystem{'uts_release'});
    # Clean the subLevel in case there is an extraversion
    ($subLevel) = split(/[^0-9]/, $subLevel);
    $gSystem{'version_utsclean'} = $version . '.' . $patchLevel . '.'
                                   . $subLevel;

    $gSystem{'version_integer'} = kernel_version_integer($version, $patchLevel,
                                                         $subLevel);
    if ($gSystem{'version_integer'} < kernel_version_integer(2, 0, 0)) {
      error('You are running Linux version ' . $gSystem{'version_utsclean'}
            . '.  This product only runs on 2.0.0 and later kernels.' . "\n\n");
    }

    if (vmware_product() eq 'server') {
      $gSystem{'smp'} = 'no';
      $gSystem{'versioned'} = 'yes';
    } else {
      $gSystem{'smp'} = (direct_command(shell_string($gHelper{'uname'})
                                        . ' -v') =~ / SMP /) ? 'yes' : 'no';
      $gSystem{'versioned'} = (direct_command(shell_string($gHelper{'grep'}) . ' '
        . shell_string('^[0-9a-fA-F]\{8\} Using_Versions') . ' /proc/ksyms 2> /dev/null')
          eq '') ? 'no' : 'yes';
    }

    $gSystem{'distribution'} = distribution_info();

    if (is64BitKernel()) {
      $gSystem{'page_offset'} = '0000010000000000';
    } else {
      $gSystem{'page_offset'} = 'C0000000';
    }

    if ($gSystem{'version_integer'} >= kernel_version_integer(2, 1, 0)) {
      # 2.1.0+ kernels have hardware verify_area() support --hpreg
      my @fields;

      @fields = split(' ', direct_command(
        shell_string($gHelper{'grep'}) . ' '
        . shell_string('^[0-9a-fA-F]\{8\} printk') . ' /proc/ksyms 2> /dev/null'));
      if (not defined($fields[0])) {
        @fields = split(' ', direct_command(
	  shell_string($gHelper{'grep'}) . ' '
	  . shell_string('^[0-9a-fA-F]\{8\} \w printk') . ' /proc/kallsyms 2> /dev/null'));
      }
      if (defined($fields[0])) {
        my $page_offset;

        if ($fields[0] =~ /^([1-9a-f])/i) {
          $page_offset = uc($1).'0000000';
        } else {
	  # Probably hugemem kernel. Or something went horribly wrong.
	  # hugemem base is 02xxxxxx, but better to ignore it, as it
	  # can be virtually any value, there is no requirement about
	  # base being 4gb-2**n anymore
	  $page_offset = undef;
        }
        $gSystem{'page_offset'} = $page_offset;
      } else {
        # Unable to find page_offset: accept anything
	$gSystem{'page_offset'} = undef;
      }
    }

    # Linux kernel build bug
    $gSystem{'build_bug'} = (direct_command(shell_string($gHelper{'grep'}) . ' '
      . shell_string('^[0-9a-fA-F]\{8\} __global_cli_R__ver___global_cli')
      . ' /proc/ksyms 2> /dev/null') eq '') ? 'no' : 'yes';
  }

  # Warning, the return after the end of the if statement
  # will void everything after.
  if (vmware_product() eq 'tools-for-linux' ||
      vmware_product() eq 'tools-for-freebsd' ||
      vmware_product() eq 'tools-for-solaris') {

    $gSystem{'product'} =
      direct_command(shell_string(vmware_check_vm_app_name()) . ' -p');
    if (direct_command(shell_string(vmware_check_vm_app_name())) =~ /good/) {
      $gSystem{'invm'} = 'yes';
    } else {
      $gSystem{'invm'} = 'no';
    }
    $gSystem{'resolution'} =
      direct_command(shell_string(vmware_check_vm_app_name()) . ' -r');
    chomp($gSystem{'resolution'});
    return;
  }

  if (vmware_product() eq 'wgs' ||
      vmware_product() eq 'vserver') {
    if ($gSystem{'uts_release'} =~ m/2\.2\.14-(5|5\.0)/) {
         print wrap('You are running kernel ' . $gSystem{'uts_release'} . '. '
                    . 'There is a known issue with this specific kernel that '
                    . 'can cause corruption of memory on a system wide level '
                    . 'under heavy load, such as when running '
                    . vmware_product_name() . '.' . "\n\n" . 'We recommend '
                    . 'you download the patch from Red Hat, or upgrade your '
                    . 'kernel to 2.2.17.' . "\n" . 'See http://www.redhat.com'
                    . '/support/errata/RHBA-2000013-01.html and consult your '
                    . 'distribution\'s documentation for instructions on how '
                    . 'to upgrade your kernel.' . "\n\n", 0);
    }
  }

  # CONFIG_UMISC on 2.0 kernels
  if ($gSystem{'version_integer'} < kernel_version_integer(2, 1, 0)) {
    if (   (direct_command(shell_string($gHelper{'grep'}) . ' '
                           . shell_string('^[0-9a-fA-F]\{8\} misc_register')
                           . ' /proc/ksyms') eq '')
        || (direct_command(shell_string($gHelper{'grep'}) . ' '
                           . shell_string('^[0-9a-fA-F]\{8\} misc_deregister')
                           . ' /proc/ksyms') eq '')) {
      error('You are running a Linux kernel version '
            . $gSystem{'version_utsclean'} . ' that was not built with the '
            . 'CONFIG_UMISC configuration parameter set.  '
            . vmware_product_name() . ' will not run on this system.'
            . "\n\n");
    }
  }

  # 3Com bug on 2.0.3[45] kernels
  if (   ($gSystem{'version_integer'} >= kernel_version_integer(2, 0, 34))
      && ($gSystem{'version_integer'} <= kernel_version_integer(2, 0, 35))) {
    if (   (not (-r '/proc/ioports'))
        || (not (direct_command(shell_string($gHelper{'grep'}) . ' -i '
                                . shell_string('3c90\|3c59')
                                . ' /proc/ioports') eq ''))) {
      if (get_answer('You are running Linux version '
                     . $gSystem{'version_utsclean'} . ' possibly with a 3Com '
                     . 'networking card.  Linux kernel versions 2.0.34 and '
                     . '2.0.35 have a bug in the 3Com driver that interacts '
                     . 'badly with this product.  Specifically, your physical '
                     . 'machine will occasionally hang and will require a '
                     . 'hard reset.  This bug has been fixed in 2.0.36 and '
                     . 'later kernels.  Do you want to continue the '
                     . 'configuration anyway?', 'yesno', 'no') eq 'no') {
         exit 1;
      }
    }
  }

  # These commands are Linux-specific
  if (vmware_product() ne 'tools-for-freebsd' &&
      vmware_product() ne 'tools-for-solaris') {
    # C library
    # XXX This relies on the locale
    if (system(shell_string($gHelper{'ldd'}) . ' '
               . shell_string(vmware_vmx_app_name()) . ' | '
               . shell_string($gHelper{'grep'}) . ' -q -i '
               . shell_string('not found')) == 0) {
      print wrap('The correct version of one or more libraries needed to run '
                 . vmware_product_name()
                 . ' may be missing.  This is the output of '
                 . $gHelper{'ldd'} . ' ' . db_get_answer('BINDIR') . '/vmware:'
                 . "\n", 0);
      system(shell_string($gHelper{'ldd'}) . ' '
             . shell_string(vmware_vmx_app_name()));
      print "\n";
      query('This program cannot tell for sure, but you may need to upgrade '
            . 'libc5 to glibc before you can run ' . vmware_product_name()
            . ".\n\n"
            . 'Hit enter ' . 'to continue.', '', 0);
    }

    # Processor
    foreach my $instruction ('^cpuid', 'cmov') {
      if (direct_command(shell_string($gHelper{'grep'}) . ' '
          . shell_string($instruction) . ' /proc/cpuinfo') eq '') {
        # Read the current config file;
        open(CPUINFO, '/proc/cpuinfo')
           or error('Unable to open /proc/cpuinfo in read-mode' . "\n\n");
        my @cpuinfo = <CPUINFO>;
        close(CPUINFO);
        error('Your ' . (($gSystem{'smp'} eq 'yes') ? 'processors do'
                                                    : 'processor does') . ' not '
              . 'support the ' . $instruction . ' instruction. '
              . vmware_product_name() . ' will not run on this system.' . "\n\n"
              . 'Your /proc/cpuinfo is:' . "\n\n" . "@cpuinfo");
      }
    }
    # The "flags" field became the "features" field in 2.4.0-test11-pre5 --hpreg
    if (direct_command(shell_string($gHelper{'grep'}) . ' '
                       . shell_string('^\(flags\|features\).* tsc')
                       . ' /proc/cpuinfo') eq '') {
      error('Your ' . (($gSystem{'smp'} eq 'yes') ? 'processors do'
                                                  : 'processor does') . ' not '
            . 'have a Time Stamp Counter.  ' . vmware_product_name()
            . ' will not run on this system.' . "\n\n");
    }
  }
}

# Point the user to a URL dealing with module-related problems and exits
sub module_error {
  error('For more information on how to troubleshoot module-related problems, '
        . 'please visit our Web site at "http://www.vmware.com/download'
        . '/modules/modules.html" and "http://www.vmware.com/support/reference'
        . '/linux/prebuilt_modules_linux.html".' . "\n\n");
}

# Install a module if it suitable
# Return 1 if success, 0 if failure
sub try_module {
  my $name = shift;
  my $mod = shift;
  my $force = shift;
  my $silent = shift;
  my $dst_dir;
  my %patch;

  if (not (-e $mod)) {
    # The module does not exist
    return 0;
  }

  if (not (vmware_product() eq 'server')) {
    # Probe the module without loading it or executing its code.  It is cool
    # because it avoids problems like 'Device or resource busy'
    # Note: -f bypasses only the kernel version check, not the symbol
    # resolution
    if (system(shell_string($gHelper{'insmod'}) . ' -p '
               . ($force ? '-f ' : '') . shell_string($mod)
               . ($silent ? ' >/dev/null 2>&1' : ''))) {
      return 0;
    }
    # If we are using new module-init-tools, they just ignore
    # '-p' option, and they just loaded module into the memory.
    # Just try rmmod-ing it. Silently.
    system(shell_string($gHelper{'rmmod'}) . ' ' . shell_string($name)
    	   . ' >/dev/null 2>&1');
  }

  if (-d $cKernelModuleDir . '/'. $gSystem{'uts_release'}) {
    $dst_dir = $cKernelModuleDir . '/' . $gSystem{'uts_release'};
  } else {
    print wrap('This program does not know where to install the ' . $name
               . ' module because the "' . $cKernelModuleDir . '/'
               . $gSystem{'uts_release'} . '" directory (the usual '
               . 'location where the running kernel would look for the '
               . 'module) is missing.  Please make sure that this '
               . 'directory exists before re-running this program.'
               . "\n\n", 0);
    return 0;
  }
  create_dir($dst_dir . '/misc', 0x1);
  undef %patch;
  # Install the module with a .o extension, as the Linux kernel does
  my $modDest = $dst_dir . '/misc/' . $name;
  install_file($mod, $modDest . '.o', \%patch, 0x1);
  # install a .ko symlink for 2.6 kernels
  install_symlink($modDest . '.o', $modDest . '.ko');
  # The old installer allowed people to manually build modules without .o
  # extension.  Such modules were not removed by the old uninstaller, and
  # unfortunately, insmod tries them first.  Let's move them.
  if (file_name_exist($dst_dir . '/misc/' . $name)) {
    backup_file($dst_dir . '/misc/' . $name);
    if (not unlink($dst_dir . '/misc/' . $name)) {
      print STDERR wrap('Unable to remove the file ' . $dst_dir . '/misc/'
                        . $name . '.' . "\n\n", 0);
    }
  }

  return 1;
}

# Remove a temporary directory
sub remove_tmp_dir {
  my $dir = shift;

  if (system(shell_string($gHelper{'rm'}) . ' -rf ' . shell_string($dir))) {
    print STDERR wrap('Unable to remove the temporary directory ' . $dir . '.'
                      . "\n\n", 0);
  };
}

sub get_cc {
  $gHelper{'gcc'} = '';
  if (defined($ENV{'CC'}) && (not ($ENV{'CC'} eq ''))) {
    $gHelper{'gcc'} = internal_which($ENV{'CC'});
    if ($gHelper{'gcc'} eq '') {
      print wrap('Unable to find the compiler specified in the CC environnment variable: "'
                 . $ENV{'CC'} . '".' . "\n\n", 0);
    }
  }
  if ($gHelper{'gcc'} eq '') {
    $gHelper{'gcc'} = internal_which('gcc');
    if ($gHelper{'gcc'} eq '') {
      $gHelper{'gcc'} = internal_which('egcs');
      if ($gHelper{'gcc'} eq '') {
        $gHelper{'gcc'} = internal_which('kgcc');
        if ($gHelper{'gcc'} eq '') {
          $gHelper{'gcc'} = DoesBinaryExist_Prompt('gcc');
        }
      }
    }
  }
  print wrap('Using compiler "' . $gHelper{'gcc'}
             . '". Use environment variable CC to override.' . "\n\n", 0);
  return $gHelper{'gcc'};
}

sub get_gcc_version {
  my ($gcc) = @_;
  my $gcc_version = direct_command(shell_string($gcc)
				. ' -dumpversion');
  chomp($gcc_version);
  if ($gcc_version =~ /^(egcs-)?(\d+(\.\d+)*)/) {
    return $2;
  } else {
    print wrap('Your compiler "' . $gHelper{'gcc'} . '" version "' .
	       $gcc_version . '" is not supported ' .
	       'by this version of ' . vmware_product_name() . '.' .
	       "\n\n", 0);
    return 'no';
  }

}

# Verify gcc version, finding a better match if needed.
sub check_gcc_version {
  my ($kernel_gcc_version) = undef;

  if (open(PROC_VERSION, '</proc/version')) {
    my $line;
    if (defined($line = <PROC_VERSION>)) {
      close PROC_VERSION;
      if ($line =~ /gcc version (egcs-)?(\d+(\.\d+)*)/) {
        $kernel_gcc_version = $2;
        if ($kernel_gcc_version eq $gSystem{'gcc_version'}) {
          return 'yes';
        }
      }
    } else {
      close PROC_VERSION;
    }
  }
  my $msg;
  my $g_major = '0';
  if ($gSystem{'gcc_version'} =~ /^(\d+)\./) {
    $g_major = $1;
  }
  if (defined($kernel_gcc_version)) {
    my $k_major = '0';
    my $k_minor = '0';

    if ($kernel_gcc_version =~ /^(\d+)\.(\d+)/) {
      $k_major = $1;
      $k_minor = $2;
    }
    if ($g_major ne $k_major) {
      # Try a to find a gcc-x.y binary
      my $newGcc = internal_which("gcc-$k_major.$k_minor");
      if ($newGcc ne '') {
	# We found one, we need to update the global values.
	$gHelper{'gcc'} = $newGcc;
	$gSystem{'gcc_version'} = get_gcc_version($newGcc);
	if ($gSystem{'gcc_version'} eq 'no') {
	  return 'no';
        } else {
	  $gSystem{'gcc_version'} =~ /^(\d+)\./;
	  $g_major = $1;
	  if ($kernel_gcc_version eq $gSystem{'gcc_version'}) {
	    return 'yes';
	  }
	}
      }
    }
    $msg = 'Your kernel was built with "gcc" version "' . $kernel_gcc_version .
           '", while you are trying to use "' . $gHelper{'gcc'} .
           '" version "' . $gSystem{'gcc_version'} . '". ';
    if ($g_major ne $k_major) {
      $msg .= 'This configuration is not supported and ' .
              vmware_product_name() . ' cannot work in such configuration. ' .
              'Please either recompile your kernel with "' . $gHelper{'gcc'} .
              '" version "'. $gSystem{'gcc_version'} . '", or restart ' . $0 .
              ' with CC environment variable pointing to the "gcc" version "' .
              $kernel_gcc_version . '".' . "\n\n";
      print wrap($msg, 0);
      return 'no';
    }
    $msg .= 'This configuration is not recommended and ' .
            vmware_product_name() . ' may crash if you\'ll continue. ' .
            'Please try to use exactly same compiler as one used for ' .
            'building your kernel. Do you want to go with compiler "' .
            $gHelper{'gcc'} .'" version "' . $gSystem{'gcc_version'} .'" anyway?';
  }
  if (defined($msg) and get_answer($msg, 'yesno', 'no') eq 'no') {
    return 'no';
  }
  return 'yes';
}

# Build a module
sub build_module {
  my $name = shift;
  my $dir = shift;
  my $ideal = shift;
  my $build_dir;
  my $gcc_version;

  # Lazy initialization
  if ($gFirstModuleBuild == 1) {
    my $program;
    my $headerdir;

    foreach $program ('make', 'echo', 'tar', 'rm') {
      if (not defined($gHelper{$program})) {
        $gHelper{$program} = DoesBinaryExist_Prompt($program);
        if ($gHelper{$program} eq '') {
          return 'no';
        }
      }
    }

    if (get_cc() eq '') {
      return 'no';
    }

    $gSystem{'gcc_version'} = get_gcc_version($gHelper{'gcc'});
    if ($gSystem{'gcc_version'} eq 'no') {
      return 'no';
    }

    if (check_gcc_version() eq 'no') {
      return 'no';
    }

    # When installing the modules, kernels 2.4+ setup a symlink to the kernel
    # source directory
    $headerdir = $cKernelModuleDir . '/preferred/build/include';
    if (check_answer_headerdir($headerdir, 'default') eq '') {
      $headerdir = $cKernelModuleDir . '/' . $gSystem{'uts_release'}
                   . '/build/include';
      if (check_answer_headerdir($headerdir, 'default') eq '') {
        # Use a default usual location
        $headerdir = '/usr/src/linux/include';
      }
    }
    get_persistent_answer('What is the location of the directory of C header '
                          . 'files that match your running kernel?',
                          'HEADER_DIR', 'headerdir', $headerdir);

    $gFirstModuleBuild = 0;
  }

  print wrap('Extracting the sources of the ' . $name . ' module.' . "\n\n",
             0);
  $build_dir = make_tmp_dir($cTmpDirPrefix);

  if (system(shell_string($gHelper{'tar'}) . ' -C ' . shell_string($build_dir)
             . ' -xopf ' . shell_string($dir . '/' . $name . '.tar'))) {
    print wrap('Unable to untar the "' . $dir . '/' . $name . '.tar'
               . '" file in the "' . $build_dir . '" directory.' . "\n\n", 0);
    return 'no';
  }

  print wrap('Building the ' . $name . ' module.' . "\n\n", 0);
  if (system(shell_string($gHelper{'make'}) . ' -C '
             . shell_string($build_dir . '/' . $name . '-only')
             . ' auto-build ' . (($gSystem{'smp'} eq 'yes') ? 'SUPPORT_SMP=1 '
                                                            : '')
             . shell_string('HEADER_DIR=' . db_get_answer('HEADER_DIR')) . ' '
             . shell_string('CC=' . $gHelper{'gcc'}) . ' '
             . shell_string('GREP=' . $gHelper{'grep'}) . ' '
             . shell_string('IS_GCC_3='
             . (($gSystem{'gcc_version'} =~ /^3\./) ? 'yes' : 'no')))) {
    print wrap('Unable to build the ' . $name . ' module.' . "\n\n", 0);
    return 'no';
  }

  # Don't use the force flag: the module is supposed to perfectly load
  if (try_module($name, $build_dir . '/' . $name . '.o', 0, 1)) {
    print wrap('The module loads perfectly in the running kernel.' . "\n\n",
               0);
    remove_tmp_dir($build_dir);
    return 'yes';
  }

  # Don't remove the build dir so that the user can investiguate
  print wrap('Unable to make a ' . $name . ' module that can be loaded in the '
             . 'running kernel:' . "\n", 0);
  try_module($name, $build_dir . '/' . $name . '.o', 0, 0);
  # Try to analyze some usual suspects
  if ($gSystem{'build_bug'} eq 'yes') {
    print wrap('It appears that your running kernel has not been built from a '
               . 'kernel source tree that was completely clean (i.e. the '
               . 'person who built your running kernel did not use the "make '
               . 'mrproper" command).  You may want to ask the provider of '
               . 'your Linux distribution to fix the problem.  In the '
               . 'meantime, you can do it yourself by rebuilding a kernel '
               . 'from a kernel source tree that is completely clean.'
               . "\n\n", 0);
  } else {
    print wrap('There is probably a slight difference in the kernel '
               . 'configuration between the set of C header files you '
               . 'specified and your running kernel.  You may want to rebuild '
               . 'a kernel based on that directory, or specify another '
               . 'directory.' . "\n\n", 0);
  }
  return 'no';
}

# Converts (currently RedHat EL3 & EL4 only) version to the opaque token - if
# tokens from two kernels are identical, these two kernels are probably
# ABI compatible.
sub get_module_compatible_version {
  my $utsrel = shift;

  # RHEL3: 2.4.21-9.0.1.ELhugemem => 2.4.21-ELhugemem
  # RHEL4: 2.6.9-11.ELsmp => 2.6.9-ELsmp
  if ($utsrel =~ /^(\d+\.\d+\.\d+-)[0-9.]+\.(EL.*)$/) {
    return $1.$2;
  }
  return $utsrel;
}

# Create a list of modules suitable for the running kernel
# The kernel module loader does quite a good job when modules are versioned.
# But in the other case, we must be _very_ careful
sub get_suitable_modules {
  my $dir = shift;
  my @perfect = ();
  my @compatible = ();
  my @dangerous = ();
  my $candidate;
  my $uts_release = $gSystem{'uts_release'};
  my $uts_compatible = get_module_compatible_version($uts_release);

  foreach $candidate (internal_ls($dir)) {
    my %prop;
    my $list;

    # Read the properties file
    if (not open(PROP, '<' . $dir . '/' . $candidate . '/properties')) {
      print STDERR wrap('Unable to open the property file "' . $dir . '/'
                        . $candidate . '/properties".  Skipping this kernel.'
                        . "\n\n", 0);
      next;
    }
    undef %prop;
    while (<PROP>) {
      if (/^UtsVersion (.+)$/) {
        $prop{'UtsVersion'} = $1;
      } elsif (/^(\S+) (\S+)/) {
        $prop{$1} = $2;
      }
    }
    close(PROP);

    if (not (lc($gSystem{'smp'}) eq lc($prop{'SMP'}))) {
      # SMP does not match
      next;
    }
    if (defined($gSystem{'page_offset'}) and
        not (lc($gSystem{'page_offset'}) eq lc($prop{'PageOffset'}))) {
      # Page offset does not match
      next;
    }

    # By default module is not good for anything
    $list = undef;
    # If user asked to try all modules, do as he wishes.  I do not believe
    # that this option has any real use, it is way too dangerous.
    if ($gOption{'try-modules'} == 1) {
      $list = \@dangerous;
    }
    # If module is versioned, try "compatible" match (ModVersion is requied
    # due to 2.4.19-4GB being delivered by both SuSE8.1 and SLES8)
    if ($prop{'ModVersion'} eq 'yes' and
        $uts_compatible eq get_module_compatible_version($prop{'UtsRelease'})) {
      $list = \@compatible;
    }
    # If version matches exactly, great.  But only if UtsVersion matches,
    # otherwise it is second class match equivalent to the "compatible" match
    if ($uts_release eq $prop{'UtsRelease'}
        && (!defined($prop{'UtsVersion'})
            || $gSystem{'uts_version'} eq $prop{'UtsVersion'})) {
      $list = \@perfect;
    }
    if (defined($list)) {
      push @$list, ($candidate, $prop{'ModVersion'});
    }
  }

  return (@perfect, @compatible, @dangerous);
}

# Find the first file that exists from the list of files.
# Returns undefined if none of them exists.
sub find_first_exist {
  my $return_val;
  my $file = shift;
  while (defined $file) {
    if (-e $file) {
      $return_val = $file;
      last;
    }
    $file = shift;
  }
  return $return_val;
}

# Configure a module
sub configure_module {
  my $name = shift;
  my $mod_dir;

  if (defined($gDBAnswer{'ALT_MOD_DIR'})
      && ($gDBAnswer{'ALT_MOD_DIR'} eq 'yes')) {
    $mod_dir = db_get_answer('LIBDIR') . '/modules.new';
  } else {
    $mod_dir = db_get_answer('LIBDIR') . '/modules';
  }

  if (($name eq 'vmxnet') and (not is64BitKernel())) {
    # Figure out the correct network script.
    my $init_dir = db_get_answer('INITSCRIPTSDIR');
    my $network_path = find_first_exist("$init_dir/network",
                                        "$init_dir/networking");
    if (!defined($network_path)) {
      print wrap("Can not find $init_dir/network and $init_dir/networking.\n\n", 0);
      return 'no';
    }
    # rmmoding the pcnet32 module on RH7.1/2.4.2-2 kernel leaves the kernel
    # in an unpredictable state:  modprobing vmxnet kills the kernel (oopses),
    # reading from /proc/bus/pci/devices hangs the kernel.  So leave pcnet32
    # in place and go ahead and modprobe vmxnet.  The module will load but
    # will require a reboot to take over network duties.
    if ($gSystem{'version_integer'} != kernel_version_integer(2, 4, 2)) {
      if (!system(shell_string($gHelper{'lsmod'}) . ' | grep ^pcnet32' . '')) {
        print wrap('Unloading pcnet32 module' . "\n\n", 0);
        if (system(shell_string("$network_path") . ' stop >/dev/null 2>&1') ||
            system(shell_string($gHelper{'rmmod'}) . ' pcnet32'
                   . ' >/dev/null 2>&1')) {
          print wrap('Unable to remove the pcnet32 module while installing' .
                     ' new vmxnet.' . "\n\n", 0);
          return 'no';
        }
      }
    }
    if (!system(shell_string($gHelper{'lsmod'}) . ' | grep ^vmxnet' . '')) {
      print wrap('Unloading vmxnet module' . "\n\n", 0);
      if (system(shell_string("$network_path") . ' stop >/dev/null 2>&1') ||
          system(shell_string($gHelper{'rmmod'}) . ' vmxnet'
                 . ' >/dev/null 2>&1')) {
        print wrap('Unable to remove the vmxnet module while installing' .
                   ' new vmxnet.' . "\n\n", 0);
        return 'no';
      }
    }
  }

  if ($gOption{'compile'} == 1) {
    db_add_answer('BUILDR_' . $name, 'yes');
  } else {
    my @mod_list;

    print wrap('Trying to find a suitable ' . $name
               . ' module for your running kernel.' . "\n\n", 0);
    @mod_list = get_suitable_modules($mod_dir . '/binary');
    while ($#mod_list > -1) {
      my $candidate = shift(@mod_list);
      my $modversion = shift(@mod_list);

      # Note: When using the force flag,
      #        Non-versioned modules can load into a     versioned kernel.
      #            Versioned modules can load into a non-versioned kernel.
      #
      # Consequently, it is only safe to use the force flag if _both_ the
      # kernel and the module are versioned.
      # This is not always the case as demonstrated by bug 18371.
      #
      # I would stop using force flag immediately, it does nothing good.

      if (try_module($name,
                     $mod_dir . '/binary/' . $candidate . '/objects/'
                     . $name . '.o',
                        ($gSystem{'versioned'} eq 'yes')
                     && ($modversion eq 'yes'), 1)) {
        print wrap('The module ' . $candidate . ' loads perfectly in the '
                   . 'running kernel.' . "\n\n", 0);
        return 'yes';
      }
    }

    if ($gOption{'prebuilt'} == 1) {
      db_add_answer('BUILDR_' . $name, 'no');
      print wrap('None of the pre-built ' . $name . ' modules for '
		 . vmware_product_name() . ' is suitable for your '
		 . 'running kernel.' . "\n\n", 0);
      return 'no';
    }

    if (get_persistent_answer('None of the pre-built ' . $name . ' modules for '
			      . vmware_product_name() . ' is suitable '
                              . 'for your running kernel.  Do you want this '
                              . 'program to try to build the ' . $name
                              . ' module for your system (you need to have a '
                              . 'C compiler installed on your system)?',
                              'BUILDR_' . $name, 'yesno', 'yes') eq 'no') {
      return 'no';
    }
  }

  if (build_module($name, $mod_dir . '/source') eq 'no') {
    return 'no';
  }
  $gOption{'compile'} = 1;
  return 'yes';
}

# Determines whether a solaris driver is already configured using the provided
# driver name and alias (alias may be '' if none is required for this driver).
#  Results: yes if configured, no if not
sub solaris_driver_configured {
  my $driver = shift;
  my $alias = shift;

  if (system(shell_string($gHelper{'grep'}) . ' ' . shell_string($driver)
             . ' /etc/name_to_major > /dev/null 2>&1') == 0) {
    if ($alias eq '' ||
        direct_command('grep ' . $driver . ' /etc/driver_aliases') =~ /$alias/) {
      return 'yes';
    }
  }

  return 'no';
}

sub solaris_module_id {
   my $module=shift;
   my $moduleId=undef;

   # tail +2 skips the header line (why is it not +1?)
   open(MODINFO, 'modinfo | tail +2 |');
   while (<MODINFO>) {
     s/^\ +//;
     my @modinfo = split(/[ ]+/, $_);
     if ($module eq $modinfo[5]) {
        $moduleId=$modinfo[0];
     }
   }
   close(MODINFO);

   return $moduleId;
}

sub solaris_os_version {
  my $solVersion = direct_command(shell_string($gHelper{'uname'}) . ' -r');
  chomp($solVersion);
  my ($major, $minor) = split /\./, $solVersion;
  return ($major, $minor);
}

sub solaris_10_or_greater {
  my $answer = 'no';
  my ($major, $minor) = solaris_os_version();

  if ($major > 5 || ($major == 5 &&  $minor >= 10)) {
    $answer = 'yes';
  }

  return $answer;
}

sub configure_module_solaris {
  my $module = shift;
  my %patch;
  my $dir = db_get_answer('LIBDIR') . '/modules/binary/';
  my ($major, $minor) = solaris_os_version();

  if ($major != 5 || $minor < 9) {
    print "VMware Tools for Solaris is only available for Solaris 9 and later.\n";
    return;
  }

  if ($module eq 'vmmemctl') {
    if (is64BitKernel()) {
      print wrap('VMware Tools for Solaris does not yet support the memory '
                 . 'control driver (vmmemctl) on 64-bit systems.' . "\n\n", 0);
      return;
    }

    undef %patch;
    install_file($dir . '10/vmmemctl', '/kernel/drv/vmmemctl',
                 \%patch, 0x1);
    undef %patch;
    install_file($dir . '10/vmmemctl.conf', '/kernel/drv/vmmemctl.conf',
                 \%patch, 0x1);

    if (solaris_driver_configured('vmmemctl', '') eq 'no') {
       system(shell_string($gHelper{'add_drv'}) . ' vmmemctl >/dev/null 2>&1');
    }

    db_add_answer('VMMEMCTL_CONFED', 'yes');
  }

  if ($module eq 'vmxnet') {
    if (is64BitKernel()) {
      print wrap('The vmxnet driver will not be installed since the e1000 '
                 . 'device is the supported high performance networking '
                 . 'device for 64-bit systems.' . "\n\n", 0);
      return;
    }

    my $pcnId;
    undef %patch;

    # Remove pcn's hold on "pci1022,2000".
    if ($minor == 9) {
      # It seems we actually need to remove the pcn driver on 9 for the
      # binding of vmxnet to pci1022,2000 to take effect; just manually
      # editing /etc/driver_aliases is not enough
      system(shell_string($gHelper{'rem_drv'}) . ' pcn >/dev/null 2>&1');
    } else {
      # Note that it's okay if this fails since the module can't be removed;
      # /etc/driver_aliases will still be updated and the change will take
      # affect on reboot.
      system(shell_string($gHelper{'update_drv'}) . ' -d -i \'"pci1022,2000"\' '
                          . 'pcn >/dev/null 2>&1');
    }

    # Installation of the vmxnet driver is comprised of placing the driver in
    # /kernel/drv and adding it to the system with add_drv(1M).  add_drv(1M)
    # usually handles adding an entry to /etc/driver_aliases, loading the
    # module and invoking devfsadm(1M) to add appropriate symlinks from /dev
    # to /devices.  Here we are only concerned with installing the driver on
    # the system (this should be done regardless of whether the VM currently
    # has a vmxnet device), and save the module loading and /dev symlinks
    # until there actually is a device.  As such, we invoke add_drv(1M) with
    # the -n flag so the driver is not loaded.  Later, in our /etc/init.d
    # script, we look for the vmxnet device and invoke devfsadm(1M) manually
    # ourselves (we don't invoke modload(1M) since the module is automatically
    # loaded when the interface is brought up).  More explicitly:
    #  Here:   $ cp vmxnet /kernel/drv
    #  Here:   $ /usr/sbin/add_drv -n -m '* 0600 root sys' \
    #                              -i '"pci15ad,720" "pci1022,2000"' vmxnet
    #  init.d: $ /usr/sbin/devfsadm -i vmxnet
    install_file($dir . '10/vmxnet', '/kernel/drv/vmxnet', \%patch, 0x1);

    # Prevent adding the driver if we already have; prevents errors on two
    # successive invocations of this script
    if (solaris_driver_configured('vmxnet', 'pci15ad,720') eq 'no') {
      system(shell_string($gHelper{'add_drv'}) . ' -n -m \'* 0600 root sys\''
             . ' -i \'"pci15ad,720" "pci1022,2000"\' vmxnet >/dev/null 2>&1');
    }

    db_add_answer('VMXNET_CONFED', 'yes');
  }
}

sub configure_module_bsd {
  my $module = shift;
  my %patch;
  my $dir = db_get_answer('LIBDIR') . '/modules/binary/FreeBSD';

  if ($module eq 'vmmemctl') {
    if (is64BitKernel()) {
      if ($gSystem{'uts_version'} =~ /FreeBSD 5/) {
        undef %patch;
        install_file($dir . '5.3-amd64/vmmemctl.ko', '/boot/kernel/vmmemctl.ko',
                     \%patch, 0x1);
      } elsif ($gSystem{'uts_version'} =~ /FreeBSD 6/) {
        undef %patch;
        install_file($dir . '6.0-amd64/vmmemctl.ko', '/boot/kernel/vmmemctl.ko',
                     \%patch, 0x1);
      }
    } else {
      if ($gSystem{'uts_version'} =~ /FreeBSD 3/) {
        undef %patch;
        install_file($dir . '3.2/vmmemctl.ko', '/modules/vmmemctl.ko',
                     \%patch, 0x1);
      } elsif ($gSystem{'uts_version'} =~ /FreeBSD 4/) {
        undef %patch;
        install_file($dir . '4.0/vmmemctl.ko', '/modules/vmmemctl.ko',
                     \%patch, 0x1);
      } elsif ($gSystem{'uts_version'} =~ /FreeBSD 5/) {
        undef %patch;
        install_file($dir . '5.3-i386/vmmemctl.ko', '/boot/kernel/vmmemctl.ko',
                     \%patch, 0x1);
      } elsif ($gSystem{'uts_version'} =~ /FreeBSD 6/) {
        undef %patch;
        install_file($dir . '6.0-i386/vmmemctl.ko', '/boot/kernel/vmmemctl.ko',
                     \%patch, 0x1);
      }
    }
  }

  if ($module eq 'vmxnet') {
    my $vmxnet_confed = 'no';

    if (not is64BitKernel()) {
      if ($gSystem{'uts_version'} =~ /FreeBSD 4\.(\d+)/ &&
          $1 >= 8) {
        # Version 4.8 included because I did testing in a Free BSD 4.8 VM
        undef %patch;
        install_file($dir . '4.9/vmxnet.ko', '/modules/vmxnet.ko',
                     \%patch, 0x1);
        $vmxnet_confed = 'yes';
      } elsif ($gSystem{'uts_version'} =~ /FreeBSD 5/) {
        undef %patch;
        install_file($dir . '5.3-i386/vmxnet.ko', '/boot/kernel/vmxnet.ko',
                     \%patch, 0x1);
        $vmxnet_confed = 'yes';
      } elsif ($gSystem{'uts_version'} =~ /FreeBSD 6/) {
        undef %patch;
        install_file($dir . '6.0-i386/vmxnet.ko', '/boot/kernel/vmxnet.ko',
                     \%patch, 0x1);
        $vmxnet_confed = 'yes';
      }
    }
    if ($vmxnet_confed eq 'yes') {
      # Configure autoloading only if vmxnet_load is not mentioned in
      # loader config.  Besides that it fixes /boot/loader.conf growing
      # without limits we now honor administrator decision to disable
      # vmxnet loading.
      # We look for vmxnet_load even in the middle of line, so administrator
      # can just comment out vmxnet_load line instead of setting it to NO.
      if (not block_match('/boot/loader.conf', 'vmxnet_load=')) {
        block_append('/boot/loader.conf',
                     $cMarkerBegin,
                     'vmxnet_load="YES"' . "\n",
                     $cMarkerEnd);
      }
    }
    db_add_answer('VMXNET_CONFED', $vmxnet_confed);
  }
}

# Create a device name
sub configure_dev {
   # Call the below function with 0 flags to ensure we don't timestamp file
   configure_dev_flags(shift, shift, shift, shift, 0);
}

sub configure_dev_flags {
  my $name = shift;
  my $major = shift;
  my $minor = shift;
  my $chr = shift;
  my $flags = shift;
  my $type;
  my $typename;

  if ($chr == 1) {
    $type = 'c';
    $typename = 'character';
  }
  else {
    $type = 'b';
    $typename = 'block';
  }
  uninstall_file($name);
  if (-e $name) {
    if (-c $name) {
      my @statbuf;

      @statbuf = stat($name);
      if (   defined($statbuf[6])
          && (($statbuf[6] >> 8) == $major)
          && (($statbuf[6] & 0xFF) == $minor)
          && ($chr == 1 && ($statbuf[2] & 0020000) != 0 ||
               $chr == 0 && ($statbuf[2] & 0020000) == 0)) {
         # The device is already correctly configured
         return;
      }
    }

    if (get_answer('This program wanted to create the ' . $typename . ' device '
                   . $name . ' with major number ' . $major . ' and minor '
                   . 'number ' . $minor . ', but there is already a different '
                   . 'kind of file at this location.  Overwrite?', 'yesno',
                   'yes') eq 'no') {
      error('Unable to continue.' . "\n\n");
    }

    # mknod doesn't like when the file already exists
    unlink($name);
  }

  if (system(shell_string($gHelper{'mknod'}) . ' ' . shell_string($name) . ' '
             . shell_string($type) . ' ' . shell_string($major) . ' '
             . shell_string($minor))) {
    error('Unable to create the ' . $typename . ' device ' . $name . ' with '
          . 'major number ' . $major . ' and minor number ' . $minor . '.'
          . "\n\n");
  }
  safe_chmod(0600, $name);
  db_add_file($name, $flags);
}

# Determine whether /dev is populated dynamically
sub is_dev_dynamic {
  if (-e '/dev/.devfs' || -e '/dev/.udev.tdb' || -e '/dev/.udevdb' ) {
    # Either the devfs" or "udev" filesystem is mounted on the "/dev" directory
    return 'yes';
  }

  return 'no';
}

# Configuration related to the monitor
sub configure_mon {
  if (configure_module('vmmon') eq 'no') {
    module_error();
  }

  if (is_dev_dynamic() eq 'yes') {
    # Either the devfs" or "udev" filesystem is mounted on the "/dev" directory,
    # so the "/dev/vmmon" block device file is magically created/removed when the
    # "vmmon" module is loaded/unloaded (was bug 15571 and 72114)
  } else {
    configure_dev('/dev/vmmon', 10, 165, 1);
  }
}

# Configuration related to parallel ports
sub configure_pp {
  my $i;

  if ($gSystem{'version_integer'} < kernel_version_integer(2, 1, 127)) {
    query('You are running Linux version ' . $gSystem{'version_utsclean'}
          . ', and this kernel cannot provide ' . vmware_product_name()
          . ' with Bidirectional Parallel Port support.  A fully-featured '
          . vmware_product_name() . ' requires Linux version 2.1.127 or '
          . 'higher.' . "\n\n" . 'Without this support, '
          . vmware_product_name() . ' will run flawlessly, but will lack the '
          . 'ability to use parallel ports in a bidirectional way.  This '
          . 'means that it is possible that some parallel port devices '
          . '(scanners, dongles, ...) will not work inside a virtual machine.'
          . "\n\n" . 'Hit enter to continue.', '', 0);
    return;
  }

  if ($gSystem{'version_integer'} <= kernel_version_integer(2, 3, 9)) {
    # Those kernels don't support ppdev.  We need to supply our vmppuser module

    print wrap('Making sure that both the parport and parport_pc kernel '
               . 'services are available.' . "\n\n", 0);

    # The vmppuser module relies on the parport modules.  Let's
    # make sure it is loaded before beginning our tests
    if (direct_command(shell_string($gHelper{'grep'}) . '  '
                       . shell_string(' parport_release[^' . "\t" . ']*$')
                       . ' /proc/ksyms') eq '') {
      # This comment fixes emacs's broken syntax highlighting
      # parport support is not built in the kernel
      if (system(shell_string($gHelper{'modprobe'})
                 . ' parport >/dev/null 2>&1')) {
        query('Unable to load the parport module that is required by the '
              . 'vmppuser module.  You may want to load it manually before '
              . 're-running this program.' . "\n\n" . 'Without this support, '
              . vmware_product_name() . ' will run flawlessly, but will lack '
              . 'the ability to use parallel ports in a bidirectional way.  '
              . 'This means that it is possible that some parallel port '
              . 'devices (scanners, dongles, ...) will not work inside a '
              . 'virtual machine.' . "\n\n"
              . 'Hit enter to continue.', '', 0);
        return;
      }
    }

    # The vmppuser module relies on the parport_pc modules.  Let's
    # make sure it is loaded before beginning our tests
    if (direct_command(shell_string($gHelper{'grep'}) . '  '
                       . shell_string(' parport_pc_[^' . "\t" . ']*$')
                       . ' /proc/ksyms') eq '') {
      # This comment fixes emacs's broken syntax highlighting
      # parport_pc support is not built in the kernel
      if (system(shell_string($gHelper{'modprobe'})
                 . ' parport_pc >/dev/null 2>&1')) {
        query('Unable to load the parport_pc module that is required by the '
              . 'vmppuser module.  You may want to load it manually before '
              . 're-running this program.' . "\n\n" . 'Without this support, '
              . vmware_product_name() . ' will run flawlessly, but will lack '
              . 'the ability to use parallel ports in a bidirectional way.  '
              . 'This means that it is possible that some parallel port '
              . 'devices (scanners, dongles, ...) will not work inside a '
              . 'virtual machine.' . "\n\n" . 'Hit enter to continue.', '', 0);
        return;
      }
    }

    if (configure_module('vmppuser') eq 'no') {
      module_error();
    }

    # Try to unload the modules.  Failure is allowed because some other
    # process could be using them.
    system(shell_string($gHelper{'modprobe'})
           . ' -r parport_pc >/dev/null 2>&1');
    system(shell_string($gHelper{'modprobe'}) . ' -r parport >/dev/null 2>&1');
  }

  # The parport numbering scheme in 2.2.X is confusing:
  # Because devices can be daisy-chained on a port, the first port
  # (/proc/parport/0) is /dev/parport0, but the second one (/proc/parport/1)
  # is /dev/parport16 (not /dev/parport1), and so on...

  # This message is wrong.  I have found no evidence for this.
  # On all the linux machines that I've looked at /dev/parport1 is the 2nd port
  # That's my story and I'm sticking to it  - DavidE

  if (is_dev_dynamic() eq 'no') {
    for ($i = 0; $i < 4; $i++) {
      configure_dev_flags('/dev/parport' . $i, 99, $i, 1, 0x1);
    }
  }
}

# Configuration of the vmmemctl tools device
sub configure_vmmemctl {
  # For the time being, only ESX uses the vmmemctl driver.
  if ($gSystem{'product'} =~ /ESX/) {
    if (vmware_product() eq 'tools-for-freebsd') {
      configure_module_bsd('vmmemctl');
    } elsif (vmware_product() eq 'tools-for-solaris') {
      configure_module_solaris('vmmemctl');
    } else {
      if (configure_module('vmmemctl') eq 'no') {
        query('The memory manager driver (vmmemctl module) is used by '
              . 'VMware host software to efficiently reclaim memory from a '
              . 'virtual machine.' . "\n"
              . 'If the driver is not available, VMware host software may '
              . 'instead need to swap guest memory to disk, which may reduce '
              . 'performance.' . "\n"
              . 'The rest of the software provided by '
              . vmware_product_name()
              . ' is designed to work independently of '
              . 'this feature.' . "\n"
              . 'If you want the memory management feature,'
              . $cModulesBuildEnv
              . "\n", ' Press Enter key to continue ', 0);
        db_add_answer('VMMEMCTL_CONFED', 'no');
      } else {
        db_add_answer('VMMEMCTL_CONFED', 'yes');
      }
    }
  }
}

# Configuration of the vmhgfs tools device
sub configure_vmhgfs {
  # vmhgfs is supported only since 2.4.0
  if ($gSystem{'uts_release'} =~ /^(\d+)\.(\d+)/ &&
      $1 * 1000 + $2 >= 2004) {
    create_dir('/mnt/hgfs', 0x1);
    if (configure_module('vmhgfs') eq 'no') {
      query('The filesystem driver (vmhgfs module) is used only for the '
            . 'shared folder feature. '
            . 'The rest of the software provided by '
            . vmware_product_name()
            . ' is designed to work independently of '
            . 'this feature.' . "\n"
            . 'If you wish to have the shared folders feature,'
            . $cModulesBuildEnv
            . "\n", ' Press Enter key to continue ', 0);
      db_add_answer('VMHGFS_CONFED', 'no');
    } else {
      db_add_answer('VMHGFS_CONFED', 'yes');
    }
  }
}

#
# This function is taken from the old tools installer.
# The first argument is a complete path to a file which will be read and
# overwritten with the result.
# The second argument will be only read and should be the system file present
# before configuration.
#
sub configure_modules_dot_conf {
  my ($newModulesConf, $systemModulesConf, $ethAliases, $sounddrv, $soundopt) = @_;
  my $inline;
  my $soundfound;
  my %emittedAliases = ();

  if (not file_name_exist($systemModulesConf)) {
    my %patch;
    undef %patch;
    internal_sed('/dev/null', $systemModulesConf, 0, \%patch);
  }

  if (not open(SYSMODCONF, "<$systemModulesConf")) {
    error('Unable to open the file "' . $systemModulesConf . '".' . "\n\n");
  }

  if (not open(NEWMODCONF, ">$newModulesConf")) {
    error('Unable to open the file "' . $newModulesConf . '".' . "\n\n");
  }

  # Look for matches and selectively replace drivers
  $soundfound = 0;
  while (defined($inline = <SYSMODCONF>)) {
    if ($inline =~ /^\s*(\w+)\s+(\w+)/) {
      my ($cmd, $val) = ($1, $2);

      if ($cmd eq 'alias') {
	if ($val eq 'sound') {
	  $inline = sprintf 'alias sound %s' . "\n", $sounddrv;
	  $inline .= $soundopt;
	  $soundfound = 1;
	} elsif ($val eq 'char-major-14') {
	  $inline = sprintf 'alias char-major-14 %s' . "\n", $sounddrv;
          $inline .= $soundopt;
	  $soundfound = 1;
	} elsif (defined($ethAliases->{$val})) {
	  $inline = 'alias ' . $val . ' ' . $ethAliases->{$val} . "\n";
	  $emittedAliases{$val} = 1;
	}
      } elsif ($cmd eq 'options') {
	if ($soundfound and $inline eq $soundopt) {
	  # Silently remove sound options line if we already generated identical one
	  $inline = '';
	} elsif ($val eq $sounddrv) {
	  $inline = '# Commented out by ' . vmware_product_name() . "\n" . '# ' . $inline;
	}
      }
    }
    print NEWMODCONF $inline;
  }

  my @output;

  # Then pick up any drivers we haven't got yet.
  foreach my $key (sort keys %$ethAliases) {
    if (not defined($emittedAliases{$key})) {
      push @output, sprintf("alias %s %s\n", $key, $ethAliases->{$key});
      $emittedAliases{$key} = 1;
    }
  }
  if (keys(%emittedAliases) > 0) {
      push @output, "probeall $cNICAlias vmxnet pcnet32\n";
  }
  if ($soundfound == 0) {
    push @output, sprintf("alias char-major-14 %s\n", $sounddrv);
    push @output, $soundopt;
  }
  if (scalar @output) {
    print NEWMODCONF "# Added by " . vmware_product_name() . "\n";
    print NEWMODCONF join('', @output);
  }
  close (SYSMODCONF);
  close (NEWMODCONF);
}

#
# This is for module-init-tools (2.6 kernels)
# The first argument is a complete path to a file which will be read and
# overwritten with the result.
# The second argument will be only read and should be the system file present
# before configuration.
#
sub configure_modprobe_dot_conf {
  my ($newModprobeConf, $systemModprobeConf, $ethAliases, $sounddrv, $soundopt)
      = @_;
  my $inline;
  my $soundfound;
  my %emittedAliases = ();

  if (not file_name_exist($systemModprobeConf)) {
    my %patch;
    undef %patch;
    internal_sed('/dev/null', $systemModprobeConf, 0, \%patch);
  }

  if (not open(SYSMODCONF, "<$systemModprobeConf")) {
    error('Unable to open the file "' . $systemModprobeConf . '".' . "\n\n");
  }

  if (not open(NEWMODCONF, ">$newModprobeConf")) {
    error('Unable to open the file "' . $newModprobeConf . '".' . "\n\n");
  }

  # Look for matches and selectively replace drivers
  $soundfound = 0;
  while (defined($inline = <SYSMODCONF>)) {
    if ($inline =~ /^\s*(\w+)\s+(\w+)/) {
      my ($cmd, $val) = ($1, $2);

      if ($cmd eq 'alias') {
	if ($val eq 'sound') {
	  $inline = sprintf 'alias sound %s' . "\n", $sounddrv;
	  $inline .= $soundopt;
	  $soundfound = 1;
	} elsif ($val eq 'char-major-14') {
	  $inline = sprintf 'alias char-major-14 %s' . "\n", $sounddrv;
          $inline .= $soundopt;
	  $soundfound = 1;
	} elsif (defined($ethAliases->{$val})) {
	    $inline = 'alias ' . $val . ' ' . $ethAliases->{$val} . "\n";
	    $emittedAliases{$val} = 1;
	}
      } elsif ($cmd eq 'options') {
	if ($soundfound and $inline eq $soundopt) {
	  # Silently remove sound options line if we already generated identical one
	  $inline = '';
	} elsif ($val eq $sounddrv) {
	  $inline = '# Commented out by ' . vmware_product_name() . "\n" . '# ' . $inline;
        }
      }
    }
    print NEWMODCONF $inline;
  }

  my @output;

  push @output, "install $cNICAlias /sbin/modprobe vmxnet; /sbin/modprobe pcnet32; /bin/true\n";

  if ($soundfound == 0) {
    push @output, sprintf("alias char-major-14 %s\n", $sounddrv);
    push @output, $soundopt;
  }
  if (scalar @output) {
    print NEWMODCONF "# Added by " . vmware_product_name() . "\n";
    print NEWMODCONF join('', @output);
  }
  close (SYSMODCONF);
  close (NEWMODCONF);
}

#
# This is for module-init-tools (2.6 kernels) and hotplug
# The first argument is a complete path to a file which will be read and
# overwritten with the result.
# The second argument will be only read and should be the system file present
# before configuration.
#
sub configure_pci_dot_handmap {
  my ($newPciHandmap, $systemPciHandmap)
      = @_;
  my $inline;
  my $emittedVmnics = 0;
  my $emittedVmxnet = 0;

  if (not file_name_exist($systemPciHandmap)) {
    my %patch;
    undef %patch;
    internal_sed('/dev/null', $systemPciHandmap, 0, \%patch);
  }

  if (not open(SYSHANDMAP, "<$systemPciHandmap")) {
    error('Unable to open the file "' . $systemPciHandmap . '".' . "\n\n");
  }

  if (not open(NEWHANDMAP, ">$newPciHandmap")) {
    error('Unable to open the file "' . $newPciHandmap . '".' . "\n\n");
  }

  # Look for matches and selectively replace drivers
  while (defined($inline = <SYSHANDMAP>)) {
    if ($inline =~ /^\s*(\w+)\s+(\w+)/) {
      my ($cmd, $val) = ($1, $2);

      if ($cmd eq 'vmxnet') {
	  $inline = 'vmxnet\t\t0x000015ad 0x00000720 ' .
	      '0xffffffff 0xffffffff 0x00000000 0x00000000 0x0' . "\n";
	  $emittedVmxnet = 1;
      } elsif ($cmd eq 'vmnics') {
	  $inline = 'vmnics\t\t0x00001022 0x00002000 ' .
	      '0xffffffff 0xffffffff 0x00000000 0x00000000 0x0' . "\n";
	  $emittedVmnics = 1;
      }
    }
    print NEWHANDMAP $inline;
  }

  my @output;

  if ($emittedVmxnet == 0 ) {
      push @output, "vmxnet\t\t0x000015ad 0x00000720 0xffffffff 0xffffffff 0x00000000 0x00000000 0x0\n";
  }
  if ($emittedVmnics ==  0) {
      push @output, "vmnics\t\t0x00001022 0x00002000 0xffffffff 0xffffffff 0x00000000 0x00000000 0x0\n";
  }
  if (scalar @output) {
    print NEWHANDMAP "# Added by " . vmware_product_name() . "\n";
    print NEWHANDMAP join('', @output);
}
  close (SYSHANDMAP);
  close (NEWHANDMAP);
}


# Enumerate devices we are interested on. Returns array of 3 elements,
# where first element is number of vmxnet adapters, second element
# is number of pcnet32 adapters, and third element is number of es1371
# adapters. We do not attempt to find ISA vlance or sb.
sub get_devices_list {
  my ($vmxnet, $pcnet32, $es1371) = (0, 0, 0);
  my $line;

  # Per bug #41349 the lspci version provided by Mandrake has unwanted
  # interaction with the sound device. The alternate lspcidrake tool
  # works fine but it unnecessarily complicates the configuration script.
  # Using /proc/bus/pci/devices instead of the output of lspci/lspcidrake
  # is consistent on all supported distributions.
  if (open PCI, '</proc/bus/pci/devices') {
    while (defined($line = <PCI>)) {
      $line = lc($line);
      if ($line =~ /^[0-9a-f]*\t([0-9a-f]*)\t/) {
        my $dev = $1;
        if ($dev eq '10222000') {
          $pcnet32++;
        } elsif ($dev eq '15ad0720') {
          $vmxnet++;
        } elsif ($dev eq '12741371') {
          $es1371++;
        }
      }
    }
    close PCI;
  }
  return ($vmxnet, $pcnet32, $es1371);
}

sub is_vmxnet_present {
  my ($vmxnet);

  ($vmxnet) = get_devices_list();
  return $vmxnet ? 'yes' : 'no';
}

# Configuration of the vmxnet tools network device
sub write_module_config {
  my ($vmxnet, $pcnet32, $es1371) = get_devices_list();
  my %ethernet = ();
  my $ethidx = 0;
  my $sounddrv;
  my $soundopt;

  if (is64BitKernel()) {
    db_add_answer('VMXNET_CONFED', 'no');
    $vmxnet = 0;
  } else {
    if (configure_module('vmxnet') eq 'no') {
      query('The fast network device driver (vmxnet module) is used only for '
            . 'our fast networking interface. '
            . 'The rest of the software provided by '
            . vmware_product_name()
            . ' is designed to work independently of '
            . 'this feature.' . "\n"
            . 'If you wish to have the fast network driver enabled,'
            . $cModulesBuildEnv
            . "\n", ' Press Enter key to continue ', 0);
      db_add_answer('VMXNET_CONFED', 'no');
      $vmxnet = 0;
    } else {
      my $i;

      db_add_answer('VMXNET_CONFED', 'yes');
      for ($i = 0; $i < $vmxnet; $i++) {
        $ethernet{'eth' . $ethidx} = $cNICAlias;
        $ethidx++;
      }
    }
  }

  if ($pcnet32) {
    my $i;

    for ($i = 0; $i < $pcnet32; $i++) {
      $ethernet{'eth' . $ethidx} = $cNICAlias;
      $ethidx++;
    }
  }
  if ($es1371) {
    $sounddrv = 'es1371';
    # No sound options for es1371
    $soundopt = '';
  } else {
    $sounddrv = 'sb';
    # Assume soundblaster if no es1371 found
    if ($gSystem{'version_integer'} < kernel_version_integer(2, 2, 0)) {
      $soundopt = 'options sb io=0x220 irq=5 dma=1,5' . "\n";
    } else {
      $soundopt = 'options sb io=0x220 irq=5 dma=1 dma16=5 mpu_io=0x330' . "\n";
    }
  }
  # Save the files we have to change.
  my $modules_file = file_name_exist('/etc/conf.modules') ?
                     '/etc/conf.modules' : '/etc/modules.conf';

  backup_file_to_restore($modules_file, 'MODULES_CONF');

  configure_modules_dot_conf($modules_file, $modules_file . $cBackupExtension,
			     \%ethernet, $sounddrv, $soundopt);
  if (file_name_exist('/etc/modprobe.conf')) {
      my $modprobe_file = '/etc/modprobe.conf';
      backup_file_to_restore($modprobe_file, 'MODPROBE_CONF');
      configure_modprobe_dot_conf($modprobe_file,
                                  $modprobe_file . $cBackupExtension,
			          \%ethernet, $sounddrv, $soundopt);
  }
  if (file_name_exist('/etc/hotplug/pci.handmap')) {
      my $handmap_file = '/etc/hotplug/pci.handmap';
      backup_file_to_restore($handmap_file, 'PCI_HANDMAP');
      configure_pci_dot_handmap($handmap_file,
				$handmap_file . $cBackupExtension);
  }
}


#
# xserver_bin
#
# Try to find the path to the X binary.
# First, an exception for solaris tools.
# Next, try the $PATH.
# Finally, try /usr/X11R6/bin. Most XFree86 and Xorg 6.x installs use this.
#
sub xserver_bin {
  my $path;

  if (vmware_product() eq 'tools-for-solaris') {
    if (-e '/usr/X11/bin') {
      return '/usr/X11/bin';
    } else {
      return '';
    }
  }

  $path = internal_which('X');
  if ($path ne '') {
    return internal_dirname($path);
  }

  if (-e '/usr/X11R6/bin') {
    return '/usr/X11R6/bin';
  }

  return '';
}

sub xserver_xorg {
  return xserver_bin() . '/Xorg';
}

sub xserver4 {
  return xserver_bin() . '/XFree86';
}

sub xserver3 {
  return xserver_bin() . '/XF86_VMware';
}

sub xconfig_file_abs_path {
  my $xconfig_path = shift;
  my $xconfig_file_name = shift;
  return $xconfig_path . '/' . $xconfig_file_name;
}

#
# path_compare(dir, path1, path2)
#
# Compare the two paths, and return true if they are identical
# Evaluate the paths with respect to the passed in directory
#
sub path_compare {
  my ($dir, $path1, $path2) = @_;

  # Prepend directory for relative paths
  $path1 =~ s|^([^/])|$dir/$1|;
  $path2 =~ s|^([^/])|$dir/$1|;

  # Squash out ..'s in paths
  while ($path1 =~ /\/.*\/\.\.\//) {
    $path1 =~ s|/[^/]*/\.\./|/|;
  }

  while ($path2 =~ /\/.*\/\.\.\//) {
    $path2 =~ s|/[^/]*/\.\./|/|;
  }

  # Squash out .'s in paths
  while ($path1 =~ /\/\.\//) {
    $path1 =~ s|/\./|/|;
  }

  while ($path2 =~ /\/\.\//) {
    $path2 =~ s|/\./|/|;
  }

  # Squash out //'s in paths
  while ($path1 =~ /\/\//) {
    $path1 =~ s|//|/|;
  }

  while ($path2 =~ /\/\//) {
    $path2 =~ s|//|/|;
  }

  if ($path1 eq $path2) {
    return 'yes';
  } else {
    return 'no';
  }
}

# check_link
# Checks that a given link is pointing to the given file.
sub check_link {
  my $file = shift;
  my $link = shift;
  my $linkDest;
  my $dirname;
  $linkDest = readlink($link);
  if (!defined $linkDest) {
    return 'no';
  }
  $dirname = internal_dirname($link);
  return path_compare($dirname, $linkDest, $file);
}

# Install one symbolic link
sub install_symlink {
  my $to = shift;
  my $name = shift;

  uninstall_file($name);
  if (file_check_exist($name)) {
    return;
  }
  # The file could be a symlink to another location.  Remove it
  unlink($name);
  if (not symlink($to, $name)) {
    error('Unable to create symbolic link "' . $name . '" pointing to file "'
          . $to . '".' . "\n\n");
  }
  db_add_file($name, 0);
}

my $gLinkCount = 0;
sub symlink_if_needed {
  my $file = shift;
  my $link = shift;
  if (file_name_exist($file)) {
    if (-l $link && check_link($file, $link) eq 'yes') {
      return;
    }
    $gLinkCount = $gLinkCount + 1;
    backup_file_to_restore($link, 'LINK_' . $gLinkCount);
    install_symlink($file, $link);
  }
}

sub set_uid_X_server {
  my $x_server_file = shift;
  if (!-u $x_server_file) {
    safe_chmod(04711, $x_server_file);
  }
}

sub split_X_version {

  my $xversionAll = shift;
  my $major;
  my $minor;
  my $sub;

  if ($xversionAll =~ /(\d+)\.(\d+)\.?(\d*)/) {
    $major = $1;
    $minor = $2;
    $sub = $3 eq '' ? 0 : $3;
  } else {
    $major = 0;
    $minor = 0;
    $sub = 0;
  }
  return ($major, $minor, $sub);
}

sub fix_X_link {
  my $x_version = shift;
  my $x_server_link;
  my $x_server_link_bin = xserver_bin() . '/X';
  my $x_wrapper_file_name = 'Xwrapper';
  my $x_wrapper_file = xserver_bin() . '/' . $x_wrapper_file_name;
  my $x_server_file;
  my $x_server_file_name;

  if ($x_version == 3) {
      $x_server_file = xserver3();
  } elsif ($x_version == 4) {
      $x_server_file = xserver4();
  } elsif ($x_version == 6) {
      $x_server_file = xserver_xorg();
  } elsif ($x_version == 7) {
      $x_server_file = xserver_xorg();
  }

  $x_server_file_name = internal_basename($x_server_file);

  # Case 1:
  # In this case, the Xwrapper is used if /etc/X11/X exists (could be broken)
  # _and_ /usr/X11R6/bin/X points to Xwrapper.
  # In this case, the Xwrapper will execute setuid anything /etc/X11/X
  # is pointing to. So /etc/X11/X has to be pointing to the correct X
  # server, this is XFree86 if XFree 4 is used, our driver if XFree 3 is used.
  # WARNING: In this case, someone could very easily create a link /etc/X11/X
  # pointing to the Xwrapper, which, of course creates and infinite loop.
  # On SuSE, this mechanism is completely broken because Xwrapper tries to run
  # /usr/X11R6/bin/X !
  # In general, The wrapper is stupid.
  $x_server_link = '/etc/X11/X';
  if (-l $x_server_link &&
      check_link($x_wrapper_file, $x_server_link_bin) eq 'yes') {
    symlink_if_needed($x_server_file, $x_server_link);
    set_uid_X_server($x_server_file);
    return;
  }

  # Case 2:
  # This case is often encountered on a SuSE system.
  # Where /var/X11R6/bin/X is a little like /etc/X11/X but the Xwrapper is
  # never used on a SuSE system, of course, there could be special cases.
  # We might be tempted to zap the use of this var place
  # but startx checks for X link and refuses to start if not present in var.
  # Of course, it doesn't check where it points to :-)
  $x_server_link = '/var/X11R6/bin/X';
  if (-d internal_dirname($x_server_link)) {
    symlink_if_needed($x_server_file, $x_server_link);
    symlink_if_needed($x_server_link, $x_server_link_bin);
    set_uid_X_server($x_server_file);
    return;
  }

  # Case 3:
  # All the remaining cases, where the /usr/X11R6/bin/X bin link should be
  # pointing to a setuid root X server.
  $x_server_link = '/usr/X11R6/bin/X';
  symlink_if_needed($x_server_file, $x_server_link_bin);
  set_uid_X_server($x_server_file);
}

sub xorg {
  my $xconfig_path = '/etc/X11';
  my $xconfig_file_name = 'xorg.conf';
  my $xversion = 6;
  my $xversionAll = '';
  my $xserver_link = '';
  my $major;
  my $minor;
  my $sub;

  $xversionAll = direct_command(shell_string(xserver_xorg()) . ' -version 2>&1') =~
    /X Protocol Version 11.* Release (\d+\.\d+)/ ? $1 : '0.0.0';

  if (defined $ENV{'XORGCONFIG'} && file_name_exist('/etc/X11/' .
      $ENV{'XORGCONFIG'})) {
    $xconfig_path = '/etc/X11';
    $xconfig_file_name = $ENV{'XORGCONFIG'};
  } elsif (defined $ENV{'XORGCONFIG'} &&
           file_name_exist('/usr/X11R6/etc/X11/' . $ENV{'XORGCONFIG'})) {
    $xconfig_path = '/usr/X11R6/etc/X11';
    $xconfig_file_name = $ENV{'XORGCONFIG'};
  } elsif (file_name_exist('/etc/X11/xorg.conf-4')) {
    $xconfig_path = '/etc/X11';
    $xconfig_file_name = 'xorg.conf-4';
  } elsif (file_name_exist('/etc/X11/xorg.conf')) {
    $xconfig_path = '/etc/X11';
    $xconfig_file_name = 'xorg.conf';
  } elsif (file_name_exist('/etc/xorg.conf')) {
    $xconfig_path = '/etc';
    $xconfig_file_name = 'xorg.conf';
  } elsif (file_name_exist('/usr/X11R6/etc/X11/xorg.conf-4')) {
    $xconfig_path = '/usr/X11R6/etc/X11';
    $xconfig_file_name = 'xorg.conf-4';
  } elsif (file_name_exist('/usr/X11R6/etc/X11/xorg.conf')) {
    $xconfig_path = '/usr/X11R6/etc/X11';
    $xconfig_file_name = 'xorg.conf';
  } elsif (file_name_exist('/usr/X11R6/lib/X11/xorg.conf-4')) {
    $xconfig_path = '/usr/X11R6/lib/X11';
    $xconfig_file_name = 'xorg.conf-4';
  } elsif (file_name_exist('/usr/X11R6/lib/X11/xorg.conf')) {
    $xconfig_path = '/usr/X11R6/lib/X11';
    $xconfig_file_name = 'xorg.conf';
  }

  print wrap("\n\n" . 'Detected X.org version ' . $xversionAll . '.'
             . "\n\n", 0);

  ($major, $minor, $sub) = split_X_version($xversionAll);

  # If there is an existing driver, replace it by ours.
  if ($major == 6) {
    # If there is an existing driver replace it by ours, backing up the existing driver.
    backup_file_to_restore($gXVideoDriverFile, 'OLD_X4_DRV');
    backup_file_to_restore($gXMouseDriverFile, 'OLD_X4_MOUSEDRV');

    # Install the drivers.
    my %p;
    undef %p;
    if ($minor == 7) {
      install_file(db_get_answer('LIBDIR')  . '/configurator/XOrg/6.7.x' .
		   ($gIs64BitX ? '_64' : '') . '/vmware_drv.o',
		   $gXVideoDriverFile, \%p, 1);
      install_file(db_get_answer('LIBDIR')  . '/configurator/XOrg/6.7.x' .
		   ($gIs64BitX ? '_64' : '') . '/vmmouse_drv.o',
		   $gXMouseDriverFile, \%p, 1);
    } elsif ($minor == 8) {
      # Solaris is an early adopter and is using .so drivers on 6.8.x
      my $suffix = vmware_product() eq 'tools-for-solaris' ? '.so' : '.o';

      install_file(db_get_answer('LIBDIR')  . '/configurator/XOrg/6.8.x' .
		   ($gIs64BitX ? '_64' : '') . '/vmware_drv' . $suffix,
		   $gXVideoDriverFile, \%p, 1);
      install_file(db_get_answer('LIBDIR')  . '/configurator/XOrg/6.8.x' .
		   ($gIs64BitX ? '_64' : '') . '/vmmouse_drv' . $suffix,
		   $gXMouseDriverFile, \%p, 1);
    } elsif ($minor == 9 && (vmware_product() eq 'tools-for-solaris'
			     || vmware_product() eq 'tools-for-linux')) {
      # The 7.0 drivers work on 6.9.x as well (see bug 92501)
      install_file(db_get_answer('LIBDIR')  . '/configurator/XOrg/7.0' .
		   ($gIs64BitX ? '_64' : '') . '/vmware_drv.so',
		   $gXVideoDriverFile, \%p, 1);
      install_file(db_get_answer('LIBDIR')  . '/configurator/XOrg/7.0' .
		   ($gIs64BitX ? '_64' : '') . '/vmmouse_drv.so',
		   $gXMouseDriverFile, \%p, 1);
    } else {
      print wrap("\n\n" . 'No drivers for X.org version: ' . $xversionAll . '.'
		   . "\n\n", 0);
    }
    fix_X_link('6');
  } elsif ($major == 7 && (vmware_product() eq 'tools-for-solaris'
			   || vmware_product() eq 'tools-for-linux')) {
    if ($minor == 0) {
      my $xorg_modules_dir = xorg_find_modules_dir();
      $gXMouseDriverFile = $xorg_modules_dir . '/input/vmmouse_drv.so';
      $gXVideoDriverFile = $xorg_modules_dir . '/drivers/vmware_drv.so';

      # If there is an existing driver replace it by ours, backing up the existing
      # driver.
      backup_file_to_restore($gXVideoDriverFile, 'OLD_X4_DRV');
      backup_file_to_restore($gXMouseDriverFile, 'OLD_X4_MOUSEDRV');
      my %p;
      undef %p;
      install_file(db_get_answer('LIBDIR')  . '/configurator/XOrg/7.0' .
		   ($gIs64BitX ? '_64' : '') . '/vmware_drv.so',
		   $gXVideoDriverFile, \%p, 1);
      install_file(db_get_answer('LIBDIR')  . '/configurator/XOrg/7.0' .
		   ($gIs64BitX ? '_64' : '') . '/vmmouse_drv.so',
		   $gXMouseDriverFile, \%p, 1);
    }
  } else {
    print wrap("\n\n" . 'No drivers for X.org version: ' . $xversionAll . '.'
	       . "\n\n", 0);
  }
  return ($xversion, xconfig_file_abs_path($xconfig_path, $xconfig_file_name),
          $xversionAll);
}

# Different xorg installations may store their modules in different places.
sub xorg_find_modules_dir {
  my $modDir = '/usr/lib64/xorg/modules';
  if (-d $modDir) {
    return $modDir;
  } else {
    $modDir = '/usr/lib/xorg/modules';
    if (-d $modDir) {
      return $modDir;
    }
  }
  return get_persistent_answer('What is the location of the directory which '
			       . 'contains your XOrg modules?',
			       'XORGMODULEDIR', 'dirpath_existing', $modDir);
}

sub xfree_4 {
  my $xconfig_path;
  my $xconfig_file_name;
  my $xversionAll = '';
  my $xserver_link = '';
  my $major;
  my $minor;
  my $sub;

  $xversionAll = direct_command(shell_string(xserver4()) . ' -version 2>&1') =~
    /XFree86 Version (\d+\.\d+\.?\d*)/ ? $1: '0.0.0';

  # This search order is issued from the XF86Config man page.
  if (defined $ENV{'XF86CONFIG'} &&
      file_name_exist('/etc/X11/' . $ENV{'XF86CONFIG'})) {
    $xconfig_path = '/etc/X11';
    $xconfig_file_name = $ENV{'XF86CONFIG'};
  } elsif (defined $ENV{'XF86CONFIG'} &&
           file_name_exist('/usr/X11R6/etc/X11/' . $ENV{'XF86CONFIG'})) {
    $xconfig_path = '/usr/X11R6/etc/X11';
    $xconfig_file_name = $ENV{'XF86CONFIG'};
  } elsif (file_name_exist('/etc/X11/XF86Config-4')) {
    $xconfig_path = '/etc/X11';
    $xconfig_file_name = 'XF86Config-4';
  } elsif (file_name_exist('/etc/X11/XF86Config')) {
    # In this case, we are in the situation of having a mix between
    # XFree 3 and XFree 4, which is usually the case on RH 7.x and
    # Mandrake 7.x systems. As far as the syntax is concerned, XF86Config
    # is the 3.x version and XF86Config-4 is the 4.x version.
    # fix_X_conf patches some of the fields of the old config file into the new
    # one. There are issues if 3.x syntax fields are patched in a 4.x config
    # file. By providing a non existing file fix_X_conf will generate a correct
    # one or if the XF86Config file has the XFree 4 syntax, we can use it.
    # See bug 23196.
    # --Jeremy Bar
    $xconfig_path = '/etc/X11';
    if (direct_command(shell_string($gHelper{'grep'}) . ' '
                       . shell_string('.*') . ' '
                       . '/etc/X11/XF86Config') =~ /Section\s+\"ServerLayout\"/i) {
      $xconfig_file_name = 'XF86Config';
    } else {
      $xconfig_file_name = 'XF86Config-4';
    }
  } elsif (file_name_exist('/etc/XF86Config')) {
    $xconfig_path = '/etc';
    $xconfig_file_name = 'XF86Config';
  } elsif (file_name_exist('/usr/X11R6/etc/X11/XF86Config-4')) {
    $xconfig_path = '/usr/X11R6/etc/X11';
    $xconfig_file_name = 'XF86Config-4';
  } elsif (file_name_exist('/usr/X11R6/etc/X11/XF86Config')) {
    $xconfig_path = '/usr/X11R6/etc/X11';
    $xconfig_file_name = 'XF86Config';
  } elsif (file_name_exist('/usr/X11R6/lib/X11/XF86Config')) {
    # FreeBSD 5.2 after running xf86config in graphic mode
    $xconfig_path = '/usr/X11R6/lib/X11';
    $xconfig_file_name = 'XF86Config';
  } else {
    # X config file not found
    return (4, undef, $xversionAll);
  }

  if (defined $xconfig_file_name) {
     print wrap("\n\n" . 'Detected XFree86 version ' . $xversionAll . '.'
                . "\n\n", 0);
  }

  # If there is an existing driver, replace it by ours.
  backup_file_to_restore($gXVideoDriverFile, 'OLD_X4_DRV');
  if (file_name_exist($gXVideoDriverFile)) {
      unlink $gXVideoDriverFile;
  }

  ($major, $minor, $sub) = split_X_version($xversionAll);
  if ($major == 4) {
    if ($minor == 2) {
      # For XFree 4.2.x, we need to replace xaa and shadowfb
      my $xaaDrv = '/usr/X11R6/lib/modules/libxaa.a';
      my $shadowFbDrv = '/usr/X11R6/lib/modules/libshadowfb.a';
      backup_file_to_restore($xaaDrv, 'OLD_X4_XAA_DRV');
      backup_file_to_restore($shadowFbDrv, 'OLD_X4_SHADOW_FB_DRV');
      unlink $xaaDrv;
      unlink $shadowFbDrv;
      my %p;
      undef %p;
      install_file(db_get_answer('LIBDIR')
                   . '/configurator/XFree86-4/4.2.x/libxaa.a',
                   $xaaDrv, \%p, 1);
      install_file(db_get_answer('LIBDIR')
                   . '/configurator/XFree86-4/4.2.x/libshadowfb.a',
                   $shadowFbDrv, \%p, 1);
      install_file(db_get_answer('LIBDIR')
                   . '/configurator/XFree86-4/4.2.x/vmware_drv.o',
                   $gXVideoDriverFile, \%p, 1);
    } elsif ($minor > 2) {
      # In this case, all the XAA and ShadowFB changes are present
      # in the XFree Code and we only need to install the latest
      # driver.
      my %p;
      undef %p;
      install_file(db_get_answer('LIBDIR') . '/configurator/XFree86-4/4.3.x' .
		   ($gIs64BitX ? '_64' : '') . '/vmware_drv.o',
		   $gXVideoDriverFile, \%p, 1);
    } elsif ($minor < 2) {
      # The default, install the X free 4 driver which works with
      # the first versions of X.
      my %p;
      undef %p;
      install_file(db_get_answer('LIBDIR')
                   . '/configurator/XFree86-4/4.x/vmware_drv.o',
                   $gXVideoDriverFile, \%p, 1);
    }
    # Absolute pointing device.
    if ($major == 4 && $minor == 2) {
      my %p;
      undef %p;
      install_file(db_get_answer('LIBDIR')
		   . '/configurator/XFree86-4/4.2.x/vmmouse_drv.o',
		   $gXMouseDriverFile, \%p, 1);
    } elsif ($major == 4 && $minor == 3) {
      my %p;
      undef %p;
      if ($gIs64BitX) {
        install_file(db_get_answer('LIBDIR')
		     . '/configurator/XFree86-4/4.3.x_64/vmmouse_drv.o',
		     $gXMouseDriverFile, \%p, 1);
      } else {
	# 32-bit 4.3 mouse driver is the same as 32-bit 4.2 mouse driver.
        install_file(db_get_answer('LIBDIR')
		     . '/configurator/XFree86-4/4.2.x/vmmouse_drv.o',
		     $gXMouseDriverFile, \%p, 1);
      }
    }
    fix_X_link('4');
  } else {
    error ('Problem extracting version of XFree 4' . "\n\n");
  }
  return (4, xconfig_file_abs_path($xconfig_path, $xconfig_file_name),
          $xversionAll);
}

sub xfree_3 {
  my $xconfig_path = '/etc';
  my $xconfig_file_name = 'XF86Config';
  my $xversion = 3;
  my $xversionAll = 0;
  my $xserver3default = xserver_bin() . '/XF86_VGA16';
  my $xserver_link = '';

  $xversionAll = file_name_exist($xserver3default) ?
              direct_command(shell_string($xserver3default) .
                             ' -version 2>&1') =~
                             /XFree86 Version (\d+\.\d+\.?\d*)/ ? $1: '3.0'
                             : '3.0';

  if (file_name_exist('/etc/XF86Config')) {
    $xconfig_path = '/etc';
    $xconfig_file_name = 'XF86Config';
  } elsif (file_name_exist('/usr/X11R6/lib/X11/XF86Config') &&
           (not -l '/usr/X11R6/lib/X11/XF86Config')) {
    $xconfig_path = '/usr/X11R6/lib/X11';
    $xconfig_file_name = 'XF86Config';
  } else {
    $xconfig_path = '/etc';
    $xconfig_file_name = 'XF86Config';
  }
  print wrap("\n\n" . 'Detected XFree86 version ' . $xversionAll . '.'
             . "\n\n", 0);

  if (file_name_exist(xserver3())) {
    backup_file(xserver3());
    unlink xserver3();
  }

  if (vmware_product() eq 'tools-for-freebsd' &&
      $gSystem{'uts_release'} =~ /^(\d+)\.(\d+)/ &&
      $1 >= 4 && $2 >= 5) {
    my %p;
    undef %p;
    install_file(db_get_answer('LIBDIR')
                 . '/configurator/XFree86-3/XF86_VMware_4.5',
                 xserver3(), \%p, 1);
  } else {
    my %p;
    undef %p;
    install_file(db_get_answer('LIBDIR')
                 . '/configurator/XFree86-3/XF86_VMware',
                 xserver3(), \%p, 1);
  }

  fix_X_link('3');
  return ($xversion, xconfig_file_abs_path($xconfig_path, $xconfig_file_name),
          $xversionAll);
}

sub fix_mouse_file {
  my $mouse_file = '/etc/sysconfig/mouse';
  #
  # If gpm supports imps2, use that as the gpm mouse driver
  # for both X & gpm. If gpm doesn't support imps2, or isn't set
  # in this mode, the mouse will be erratic when exiting X if
  # X was set to use imps2
  #
  my $enableXImps2 = 'no';
  my $GPMBinary = internal_which('gpm');
  if (file_name_exist($GPMBinary) && file_name_exist($mouse_file)) {
    my $enableGpmImps2;

    if (vmware_product() eq 'tools-for-solaris') {
      $enableGpmImps2 =
        (system(shell_string($GPMBinary) . ' -t help | ' . $gHelper{'grep'}
                . ' imps2 > /dev/null 2>&1')) == 0 ? 'yes': 'no';
    } else {
      $enableGpmImps2 =
        (system(shell_string($GPMBinary) . ' -t help | '
                . $gHelper{'grep'} . ' -q imps2')) == 0 ? 'yes': 'no';
    }
    $enableXImps2 = $enableGpmImps2;

    if ($enableGpmImps2 eq 'yes' ) {
      backup_file_to_restore($mouse_file, 'MOUSE_CONF');
      unlink $mouse_file;
      my %p;
      undef %p;
      $p{'^MOUSETYPE=.*$'} = 'MOUSETYPE=imps2';
      $p{'^XMOUSETYPE=.*$'} = 'XMOUSETYPE=IMPS/2';
      internal_sed($mouse_file . $cBackupExtension,
                   $mouse_file, 0, \%p);
    }
  }
  return $enableXImps2;
}

# Create a list of available resolutions for the VMware virtual monitor
sub get_suitable_resolutions {
  my $xf86config = shift;
  my @list;
  my $in;
  my $identifier;

  open(XF86CONFIG, '<' . $xf86config) or
   error('Unable to open the XFree86 configuration file "'
         . $xf86config . '" in read-mode.' . "\n\n");

  $in = 0;
  while (<XF86CONFIG>) {
    if (/^[ \t]*Section[ \t]*"Monitor"[ \t]*$/) {
      $in = 1;
      $identifier = '';
      @list = ();
    } elsif ($in) {
      if (/^[ \t]*Identifier[ \t]*"(\S+)"[ \t]*$/) {
        $identifier = $1;
      } elsif (/^[ \t]*ModeLine[ \t]*(\S+)[ \t]*(\S+)[ \t]*(\S+)[ \t]*(\S+)[ \t]*(\S+)[ \t]*(\S+)[ \t]*(\S+)[ \t]*(\S+)[ \t]*(\S+)[ \t]*(\S+)[ \t]*$/) {
        push(@list, ($1, $3, $7));
      } elsif (/^[ \t]*EndSection[ \t]*$/) {
        if ($identifier eq 'vmware') {
          last;
        }
        $in = 0;
      }
    }
  }

  close(XF86CONFIG);

  return @list;
}

# Determine the name of the maximum available resolution that can fit in the
# VMware virtual monitor
sub get_best_resolution {
  my $xf86config = shift;
  my $width = shift;
  my $height = shift;
  my @avail_modes;
  my $best_name;
  my $best_res;

  @avail_modes = get_suitable_resolutions($xf86config);

  $best_name = '';
  $best_res = -1;
  while ($#avail_modes > -1) {
    my $mode_name = shift(@avail_modes);
    my $mode_width = shift(@avail_modes);
    my $mode_height = shift(@avail_modes);

    if (($mode_width < $width)
        && ($mode_height < $height)
        && ($mode_width * $mode_height > $best_res)) {
      $best_res = $mode_width * $mode_height;
      $best_name = $mode_name;
    }
  }
  return $best_name;
}

# Sort available resolutions for the VMware virtual monitor in increasing order
sub sort_resolutions {
  my $xf86config = shift;
  my @avail_modes;
  my %resolutions;
  my $res;
  my $names;

  @avail_modes = get_suitable_resolutions($xf86config);

  undef %resolutions;
  while ($#avail_modes > -1) {
    my $mode_name = shift(@avail_modes);
    my $mode_width = shift(@avail_modes);
    my $mode_height = shift(@avail_modes);

    $resolutions{$mode_width * $mode_height} .= $mode_name . ' ';
  }

  $names = '';
  foreach $res (sort { $a <=> $b } keys %resolutions) {
    $names .= $resolutions{$res};
  }
  if (not ($names eq '')) {
    chomp($names);
  }
  return $names;
}

#
# Try to determine the current screen size
#
sub get_screen_mode {
  my $xversion = shift;
  my $best_resolution = '';
  my $chosen_resolution = '';
  my $suggested_choice = 3;
  my $i = 1;
  my $n;
  my $mode;
  my $choice;
  my @mode_list;
  my $width;
  my $height;
  my $cXPreviousResolution = 'X_PREVIOUS_RES';
  my $cXConfigFile = db_get_answer('LIBDIR') . '/configurator/XFree86-'
                     . ($xversion >= 4 ? '4' : $xversion) . '/XF86Config'
                     . ($xversion >= 4 ? '-4': '');

  #
  # Set mode according to what was previously chosen in case of an upgrade
  # or ask the user a valid range of resolutions.
  #
  if (defined(db_get_answer_if_exists($cXPreviousResolution))) {
    if (get_answer("\n\n" .
                   'Do you want to change your guest X resolution? (yes/no)',
                   'yesno', 'no') eq 'no') {
      return db_get_answer($cXPreviousResolution);
    }
  }

  ($width, $height) = split(' ', $gSystem{'resolution'});

  $best_resolution =
    get_best_resolution($cXConfigFile, $width, $height);

  @mode_list = split(' ', sort_resolutions($cXConfigFile));

  $n = scalar @mode_list;

  print wrap("\n" . 'Please choose '
             . 'one of the following display sizes (1 - ' . $n . '):' . "\n\n",
             0);
  foreach $mode (@mode_list) {
    my $header;
    if ($best_resolution eq $mode) {
      $suggested_choice = $i;
      $header = '<';
    } else {
      $header = ' ';
    }
    print wrap('[' . $i . ']' . $header . ' ' . $mode . "\n", 0);
    $i = $i + 1;
  }

  $gMaxNumber = $n;
  $gAnswerSize{'number'} = length($gMaxNumber);
  $choice = get_persistent_answer('Please enter a number between 1 and ' . $n
                                  . ':' . "\n\n", 'XRESNUMBER', 'number',
                                  $suggested_choice);

  $chosen_resolution = $mode_list[$choice - 1];
  db_add_answer($cXPreviousResolution, $chosen_resolution);
  return $chosen_resolution;
}

#
# Generate a string full of "ModeLine" lines. We generate a modeline for every
# resolution from 100x100 to 2000x2000 in 100 pixel steps in both directions.
#
sub lots_of_modelines {
    my $ret;
    my $width = 100;
    while ($width <= 2000) {
	my $height = 100;
	while ($height <= 2000) {
	    $ret .= '    ModeLine "' . $width . 'x' . $height .'" 100 ';
	    $ret .= $width . " ";
	    $ret .= ($width + 100) . " " . ($width + 200) . " " . ($width + 300) . " ";
	    $ret .= $height . " ";
	    $ret .= ($height + 100) . " " . ($height + 200) . " " . ($height + 300);
	    $ret .= "\n";
	    $height += 100;
	}
	$width += 100;
    }
    return $ret;
}


#
# The first argument is a complete path to a new xconfig file
# The second argument will be only read and should be current xconfig file
# The third argument is the version of XFree86
# The fourth is a boolean informing weather the Imwheel mouse is used
# in gpm or not.
#
sub fix_X_conf {
  my ($newXF86Config, $existingXF86Config, $xversion, $enableXImps2,
  $xversionAll) = @_;

  my $inSection = 0;
  my $inDevice = 0;
  my $inMonitor = 0;
  my @currentSection;
  my $sectionLine;
  my $sectionName;
  my $mouseRegex = '^\s*driver\s+\"(?:mouse|vmmouse)\"';
  my $isMouseSection = 0;

  my $XFree4_scanpci = xserver_bin() . '/scanpci';
  my $major;
  my $minor;
  my $sub;
  my $line;
  my $screen_mode = get_screen_mode($xversion);

  ($major, $minor, $sub) = split_X_version($xversionAll);

  #
  # Check to see if the vmware svga driver is non-unified b/c we have to
  # specifiy the BusId in the XF86Config-4 file in that case
  #
  my $writeBusIDLine = 0;
  if ($xversion >= 4 && file_name_exist($XFree4_scanpci)) {
    my $found = 0;
    if (vmware_product() eq 'tools-for-solaris') {
      if ((system(shell_string($XFree4_scanpci) . ' | '
                 . shell_string($gHelper{'grep'})
                 . ' 0x0710 > /dev/null 2>&1')/256) == 0 ) {
        $found = 1;
      }
    } elsif ((system(shell_string($XFree4_scanpci) . ' | '
                     . shell_string($gHelper{'grep'})
                     . ' -q 0x0710')/256) == 0 ) {
      $found = 1;
    }

    if ($found == 1) {
      $writeBusIDLine = 1;
      # print wrap ('Found the device 0x0710' . "\n\n", 0);
    }
  }

  if (not open(EXISTINGXF86CONFIG, "<$existingXF86Config")) {
    error('Unable to open the file "' . $existingXF86Config . '".' . "\n\n");
  }

  if (not open(NEWXF86CONFIG, ">$newXF86Config")) {
    error('Unable to open the file "' . $newXF86Config . '".' . "\n\n");
  }

  while (defined($line = <EXISTINGXF86CONFIG>)) {
    if ($line =~ /^\s*Section\s*"([a-zA-Z]+)"/i) {
      # We only deal with lines within sections. For other lines,
      # just copy to new file.
      $sectionName = lc($1);
      $inSection = 1;
      push @currentSection, $line;
    } else {
      if ($inSection == 1) {
        if ($line =~ /^\s*EndSection/i) {
          # All lines within a section will first be read into
          # currentSection, then process those lines.
          push @currentSection, $line;

          if (($sectionName eq 'inputdevice') || ($sectionName eq 'pointer')) {
            # There are several different kinds of inputdevice section, such as
            # mouse, keyboard, and only mouse section will be re-processed,
            # others just copy to new file. 'pointer' is the mouse section name
            # for some x config file.
            $isMouseSection = 0;
            if ($sectionName eq 'pointer') {
              $isMouseSection = 1;
            }
            foreach $sectionLine (@currentSection) {
              if ($sectionLine =~ /$mouseRegex/i) {
                $isMouseSection = 1;
                last;
              }
            }

            if ($isMouseSection == 1) {
              foreach $sectionLine (@currentSection) {
                # Replace mouse driver
                if ($sectionLine =~ /^\s*Driver\s+\"(.+)\"/i) {
		  # Install a mouse driver for all X versions >= 4.2
                  if (file_name_exist($gXMouseDriverFile) &&
		      ($major > 4 || ($major == 4 && $minor >= 2))) {
                    $sectionLine =~ s/$1/vmmouse/g;
                  }
                }

                # Replace mouse protocol. There are 2 different formats for mouse
                # protocol, so should be handled seperately.
                if (($sectionLine =~ /^\s*Option\s+\"Protocol\"\s+\"(.+)\"/i) ||
                    ($sectionLine =~ /^\s*Protocol\s+\"(.+)\"/i)) {
                  my $tmpmouse = $1;
                  if (vmware_product() eq 'tools-for-freebsd') {
                    if (direct_command(shell_string($gHelper{'grep'}) . ' '
                                       . shell_string('moused_enable') . ' '
                                       . shell_string('/etc/rc.conf')) =~ /yes/i) {
                      $sectionLine =~ s/$tmpmouse/SysMouse/;
                    } else {
                      $sectionLine =~ s/$tmpmouse/ps\/2/;
                    }
                  } elsif ($enableXImps2 eq 'yes') {
                    $sectionLine =~ s/$tmpmouse/IMPS\/2/g;
                  } else {
                    $sectionLine =~ s/$tmpmouse/ps\/2/g;
                  }
                }

                # Replace mouse device. There are 2 different formats for mouse
                # device, so should be handled seperately.
                if (vmware_product() eq 'tools-for-freebsd') {
                  if (($sectionLine =~ /^\s*Option\s+\"Device\"\s+\"(.+)\"/i) ||
                      ($sectionLine =~ /^\s*Device\s+\"(.+)\"/i)) {
                    my $tmpdev = $1;
                    if (direct_command(shell_string($gHelper{'grep'}) . ' '
                                       . shell_string('moused_enable') . ' '
                                       . shell_string('/etc/rc.conf')) =~ /yes/i) {
                      $sectionLine =~ s/$tmpdev/\/dev\/sysmouse/;
                    } else {
                      $sectionLine =~ s/$tmpdev/\/dev\/psm0/;
                    }
                  }
                }

                # Solaris guests should use the PS/2 device /dev/kdmouse
                if (vmware_product() eq 'tools-for-solaris') {
                  if (($sectionLine =~ /^\s*Option\s+\"Device\"\s+\"(.+)\"/i) ||
                      ($sectionLine =~ /^\s*Device\s+\"(.+)\"/i)) {
                    my $tmpdev = $1;
                    $sectionLine =~ s/$tmpdev/\/dev\/kdmouse/;
                  }
                }

                print NEWXF86CONFIG $sectionLine;
              }
            } else {
              # In inputdevice section, if it is not mouse, just copy
              # to new file directly.
              foreach $sectionLine (@currentSection) {
                print NEWXF86CONFIG $sectionLine;
              }
            }
          } elsif ($sectionName eq 'device') {
            # Regenerate whole device section, and only one device section
            if ($inDevice == 0) {
              print NEWXF86CONFIG "Section \"Device\"\n";
              print NEWXF86CONFIG "    Identifier  \"VMware SVGA\"\n";
              if ($xversion >= 4) {
                # For config with newer format.
                print NEWXF86CONFIG "    Driver      \"vmware\"\n";
                if ($writeBusIDLine) {
                  print NEWXF86CONFIG "    BusID       \"PCI:0:15:0\"\n";
                }
              } else {
                # For config with old format.
                print NEWXF86CONFIG "    Chipset      \"generic\"\n";
              }
              print NEWXF86CONFIG "EndSection\n";
              $inDevice = 1;
            }
          } elsif ($sectionName eq 'screen') {
            # Regenerate whole screen section. All screen section will
            # be same except identifier name.
            print NEWXF86CONFIG "Section \"Screen\"\n";
            foreach $sectionLine (@currentSection) {
              if ($sectionLine =~ /^\s*Identifier\s+\"(.+)\"/i) {
                print NEWXF86CONFIG $sectionLine;
                last;
              }
            }
            if ($xversion >= 4) {
              # For config with newer format.
              print NEWXF86CONFIG <<EOF;
    Device      "VMware SVGA"
    Monitor     "vmware"
    # Don't specify DefaultColorDepth unless you know what you're
    # doing. It will override the driver's preferences which can
    # cause the X server not to run if the host doesn't support the
    # depth.
    Subsection "Display"
        # VGA mode: better left untouched
        Depth       4
        Modes       "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       8
        Modes       $screen_mode
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       15
        Modes       $screen_mode
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       $screen_mode
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       $screen_mode
        ViewPort    0 0
    EndSubsection
EndSection
EOF
            } else {
              # For config with old format.
              print NEWXF86CONFIG <<EOF;
    Driver "accel"
    Device "VMware SVGA"
    Monitor "vmware"
    Subsection "Display"
	Modes $screen_mode
#	Modes "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
#	Modes "640x480"
#	Modes "800x600"
#	Modes "1024x768"
#	Modes "1152x864"
#	Modes "1152x900"
#	Modes "1280x1024"
#	Modes "1376x1032"
#	Modes "1600x1200"
#	Modes "2364x1773"
        ViewPort 0 0
    EndSubsection
EndSection
EOF
            }
          } elsif ($sectionName eq 'monitor') {
            # Regenerate whole monitor section, and only one monitor section
            if ($inMonitor == 0) {
              print NEWXF86CONFIG <<EOF;
Section "Monitor"
    Identifier      "vmware"
    VendorName      "VMware, Inc"
    HorizSync 1-10000
    VertRefresh 1-10000

    ModeLine "640x480" 100 640 700 800 900 480 500 600 700
    ModeLine "1280x480" 100 1280 1300 1400 1500 480 500 600 700
    ModeLine "640x960" 100 640 700 800 900 960 1000 1100 1200
    ModeLine "800x600" 100 800 900 1000 1100 600 700 800 900
    ModeLine "1600x600" 100 1600 1700 1800 1900 600 700 800 900
    ModeLine "800x1200" 100 800 900 1000 1100 1200 1300 1400 1500
    ModeLine "1024x768" 100 1024 1100 1200 1300 768 800 900 1000
    ModeLine "2048x768" 100 2048 2100 2200 2300 768 800 900 1000
    ModeLine "1024x1536" 100 1024 1100 1200 1300 1536 1600 1700 1800
    ModeLine "1152x864" 100 1152 1200 1300 1400 864 900 1000 1100
    ModeLine "2304x864" 100 2304 2400 2500 2600 864 900 1000 1100
    ModeLine "1152x1728" 100 1152 1200 1300 1400 1728 1800 1900 2000
    ModeLine "1280x1024" 100 1280 1300 1400 1500 1024 1100 1200 1300
    ModeLine "2560x1024" 100 2560 2600 2700 2800 1024 1100 1200 1300
    ModeLine "1280x2048" 100 1280 1300 1400 1500 2048 2100 2200 2300
    ModeLine "1600x1200" 100 1600 1700 1800 1900 1200 1300 1400 1500
    ModeLine "3200x1200" 100 3200 3300 3400 3500 1200 1300 1400 1500
    ModeLine "1600x2400" 100 1600 1700 1800 1900 2400 2500 2600 2700
    ModeLine "1920x1400" 100 1920 2000 2100 2200 1200 1300 1400 1500
    ModeLine "3940x1400" 100 1920 2000 2100 2200 1200 1300 1400 1500
    ModeLine "1920x2800" 100 1920 2000 2100 2200 1200 1300 1400 1500
    ModeLine "1152x900" 100 1152 1200 1300 1400 900 1000 1100 1200
    ModeLine "1280x800" 100 1280 1300 1400 1500 800 900 1000 1100
    ModeLine "1376x1032" 100 1376 1400 1500 1600 1032 1100 1200 1300
    ModeLine "1400x1050" 100 1400 1500 1600 1700 1050 1100 1200 1300
    ModeLine "1680x1050" 100 1680 1700 1800 1900 1050 1100 1200 1300
    ModeLine "1920x1200" 100 1920 2000 2100 2200 1200 1300 1400 1500
    ModeLine "2364x1773" 100 2364 2400 2500 2600 1773 1800 1900 2000
EOF
	      if (vmware_product() ne 'tools-for-solaris') {
		my $modelines = lots_of_modelines();
		print NEWXF86CONFIG "$modelines";
	      }
	      print NEWXF86CONFIG "EndSection\n";
              $inMonitor = 1;
            }
          } else {
            # Copy other sections directly to new file.
            foreach $sectionLine (@currentSection) {
              print NEWXF86CONFIG $sectionLine;
            }
          }
          # Reset for next section.
          $inSection = 0;
          @currentSection = ();
        } else {
          push @currentSection, $line;
        }
      } else {
        # Copy other lines outside sections directly to new file.
        print NEWXF86CONFIG $line;
      }
    }
  }
  close (EXISTINGXF86CONFIG);
  close (NEWXF86CONFIG);
}

sub try_X_conf {
  my $xConfigFile = shift;
  my $xLogFile = shift;
  my $childPid;
  my $childStatus;
  my $vtNext;

  unless(defined(&VT_OPENQRY)) {   # find available vt
    sub VT_OPENQRY () { 0x5600; }
  }

  my $TTY0;
  open($TTY0, '/dev/tty0') or die "open /dev/tty0 : $!\n";

  my $data = pack("I", 0);
  if (ioctl($TTY0, VT_OPENQRY, $data)) {
    $vtNext = unpack("I", $data);
  } else {
    error("VT_OPENQRY ioctl() error: $!\n");
  }

  close($TTY0);

  my @xargs = ('/usr/X11R6/bin/X', ':1', 'vt' . $vtNext,
                '-xf86config',  $xConfigFile ,
                '-logfile', $xLogFile,
                '-once', '-logverbose', '3');

  if ($childPid = open(CHILD, '-|')) {
    # Run parent code, reading from child
    $SIG{ALRM} = sub { die "alarm\n" };

    my $buf;
    eval {
      alarm 5;   # Seconds
      do {
        $buf = <CHILD>;
        $childStatus = waitpid($childPid,0);
      } until $childStatus == -1;
      alarm 0;
    };

    if ($@) {
      # Propagate unexpected errors
      die unless $@ eq "alarm\n";
      # Timed out
      print wrap("\n" . 'X is running fine with the new config file.' .
                 "\n\n", 0);
      kill(15, $childPid);
      close(CHILD);
      return 1;
    } else {
      print wrap ('Error: ' . $childStatus . '. X did not start.' .
            -e $xLogFile ? ' Details in ' . $xLogFile . "\n" :
            "\n", 0);
      return 0;
    }
  } else {
    error('Can not fork: ' . "$!\n") unless defined $childPid;
    # Child code
    exec @xargs;
  }
}

sub configure_X {
  my $xversion = '';
  my $xconfig_file = '';
  my $enableXImps2 = '';
  my $xversionAll = '';
  my $xconfig_backup = '';
  my $createNewXConf = 0;
  my $addXconfToDb = 0;
  my $major;
  my $minor;
  my $sub;

  if (vmware_product() eq 'tools-for-solaris' &&
      solaris_10_or_greater() eq 'yes' &&
      direct_command(shell_string($gHelper{'svcprop'}) . ' -p options/server '
                     . 'application/x11/x11-server') =~ /Xsun/) {
     if (get_answer("\n\n" . 'You are currently using the Solaris Xsun server.  '
                    . 'VMware Tools for Solaris only supports the Xorg server '
                    . '(which can be switched to by running kdmconfig(1M) as '
                    . 'root).  Would you like to configure the Xorg server now '
                    . 'so that you have the option of switching to it in the '
                    . 'future? (yes/no)', 'yesno', 'yes') eq 'no') {
        print wrap('Skipping X configuration.' . "\n\n", 0);
        return 0;
     }
  }

  if (file_name_exist(xserver_xorg())) {
    if (is64BitElf(xserver_xorg())) {
      $gIs64BitX = 1;
      # 64-bit FreeBSD puts it's 64-bit X modules in lib not lib64
      if (vmware_product() ne 'tools-for-freebsd') {
	  $gXMouseDriverFile = "$cX64ModulesDir/input/vmmouse_drv.o";
	  $gXVideoDriverFile = "$cX64ModulesDir/drivers/vmware_drv.o";
      } else {
	  $gXMouseDriverFile = "$cXModulesDir/input/vmmouse_drv.o";
	  $gXVideoDriverFile = "$cXModulesDir/drivers/vmware_drv.o";
      }
    } else {
      # Solaris' Xorg installation is in /usr/X11 (not /usr/X11R6)
      if (vmware_product() eq 'tools-for-solaris') {
        $gXMouseDriverFile = "/usr/X11/lib/modules/input/vmmouse_drv.so";
        $gXVideoDriverFile = "/usr/X11/lib/modules/drivers/vmware_drv.so";
      } else {
        $gXMouseDriverFile = "$cXModulesDir/input/vmmouse_drv.o";
        $gXVideoDriverFile = "$cXModulesDir/drivers/vmware_drv.o";
      }
    }
    ($xversion, $xconfig_file, $xversionAll) = xorg();
  } elsif (file_name_exist(xserver4())){
    if (is64BitElf(xserver4())) {
      $gIs64BitX = 1;
      $gXMouseDriverFile = "$cX64ModulesDir/input/vmmouse_drv.o";
      $gXVideoDriverFile = "$cX64ModulesDir/drivers/vmware_drv.o";
    } else {
      $gXMouseDriverFile = "$cXModulesDir/input/vmmouse_drv.o";
      $gXVideoDriverFile = "$cXModulesDir/drivers/vmware_drv.o";
    }
    ($xversion, $xconfig_file, $xversionAll) = xfree_4();
  } elsif (file_name_exist(xserver_bin() . '/xterm')) {
    ($xversion, $xconfig_file, $xversionAll) = xfree_3();
  } else {
     print wrap ('No X install found.' . "\n\n", 0);
     return 0;
  }

  if (not defined $xconfig_file) {
    if (get_answer("\n\n" . 'Could not locate X ' . $xversionAll
                   . ' configuration file. Do you want to create a new'
                   . ' one? (yes/no)', 'yesno', 'yes') eq 'no') {
      print wrap ("\n\n" . 'Could not locate X ' . $xversionAll .
                  ' configuration file. X configuration skipped.' . "\n\n", 0);
      return 0;
    }
    $xconfig_file = "/etc/X11/XF86Config" . ($xversion >= 4 ? '-4' : '');
    $createNewXConf = 1;
  } elsif (not file_name_exist($xconfig_file)) {
    if (get_answer("\n\n" . 'The configuration file ' . $xconfig_file
                   . ' can not be found. Do you want to create a new'
                   . ' one? (yes/no)', 'yesno', 'yes') eq 'no') {
      print wrap ("\n\n" . 'The configuration file ' . $xconfig_file .
                  ' can not be found. X configuration skipped.' . "\n\n", 0);
      return 0;
    }
    $createNewXConf = 1;
  }
  if (-l $xconfig_file && !-e $xconfig_file) {
     print wrap ("\n\n" . 'The configuration file ' . $xconfig_file .
		 ' is a broken symlink. X configuration skipped.' . "\n\n", 0);
     return 0;
  }

  $enableXImps2 = fix_mouse_file();

  $xconfig_backup = $xconfig_file . $cBackupExtension;
  # -e must be also tested because we don't want to unlink
  # a non-existed file
  if ((-e $xconfig_backup) && (!-s $xconfig_backup)) {
    unlink $xconfig_backup or
      die "Failed to cleanup empty $xconfig_backup file : $!\n";
  }

  # If the X config file does not exist, we need to add it to our database.  If
  # the X config file does exist, there are two cases: 1) we created it from
  # scratch during a previous Tools configuration, or 2) we are about to or
  # have already backed up the existing X config file.  For case 1, we don't
  # want to backup the file since we created it; for case 2, we need to backup
  # the file for restoring (if the backup already exists, backup_file_to_restore
  # will do the right thing).
  if ($createNewXConf == 1) {
    $addXconfToDb = 1;
  } else {
    # Only backup the file if we didn't previously add it to the database
    if (not db_file_in($xconfig_file)) {
      backup_file_to_restore($xconfig_file, 'XCONFIG_FILE');
    }
  }

  my $tmp_dir = make_tmp_dir($cTmpDirPrefix);
  my $XF86tmp = $tmp_dir . '/XF86Config.' . $$;
  my $xLogFile = $tmp_dir . '/XF86ConfigLog.' . $$;

  if (-e $XF86tmp) {
    unlink $XF86tmp or
      die "Failed to cleanup old $XF86tmp file : $!\n";
  }
  if (-e $xLogFile) {
    unlink $xLogFile or
      die "Failed to cleanup old $xLogFile file : $!\n";
  }
  if (-e "$xLogFile.old" ) {
    unlink "$xLogFile.old" or
      die "Failed to cleanup old $xLogFile.old file : $!\n";
  }

  if ($createNewXConf == 0) {
    # Before installation, if there is no backup one, $xconfig_file will
    # be renamed to $xconfig_backup. So first $xconfig_file should be
    # checked if existed.
    if (-e $xconfig_file) {
      fix_X_conf($XF86tmp, $xconfig_file,
                 $xversion, $enableXImps2, $xversionAll);
    } else {
      fix_X_conf($XF86tmp, $xconfig_backup,
                 $xversion, $enableXImps2, $xversionAll);
    }
  } else {
  # If failed with existing $xconfig_file, try to generate a new x config
  # file with template one. The template file is also modified with fix_X_conf
  # to set right mouse protocol, driver, display, etc.
    fix_X_conf($XF86tmp, db_get_answer('LIBDIR') . '/configurator/XFree86-'
               . ($xversion >= 4 ? '4' : $xversion) . '/XF86Config'
               . ($xversion >= 4 ? '-4': ''),
               $xversion, $enableXImps2, $xversionAll);
  }

  ($major, $minor, $sub) = split_X_version($xversionAll);
  # try_X_conf has problem with old X window, please refer to bug 78985
  if (vmware_product() eq 'tools-for-linux' &&
      $major >= 4 && $minor >= 2 &&
      !try_X_conf($XF86tmp, $xLogFile)) {
    if (get_answer("\n\n" . 'The updated X config file does not work well.'
                   . ' See '. $xLogFile . ' for details. Do you want to create'
                   . ' a new one from template? Warning: if you choose to'
                   . ' create a new one, all old settings will be gone! (yes/no)',
                   'yesno', 'yes') eq 'no') {
      error('X configuration failed! The updated X config file does not ' .
            'work well. File saved as ' . $XF86tmp . '. See '. $xLogFile .
            ' for details.' . "\n\n");
      # Here temp files are not removed because user may want to check the
      # files to see what is wrong.
      return 0;
    }
    unlink $XF86tmp;
    unlink $xLogFile;
    # If test failed with $XF86tmp, try to test a new $XF86tmp from template one.
    fix_X_conf($XF86tmp, db_get_answer('LIBDIR') . '/configurator/XFree86-'
               . ($xversion >= 4 ? '4' : $xversion) . '/XF86Config'
               . ($xversion >= 4 ? '-4': ''),
               $xversion, $enableXImps2, $xversionAll);
    if (!try_X_conf($XF86tmp, $xLogFile)) {
      # Here temp files are not removed because user may want to check the
      # files to see what is wrong.
      return 0;
    }
  }
  if (system(shell_string($gHelper{'cp'}) . ' -p ' . $XF86tmp . ' ' .
      $xconfig_file)) {
    error('Unable to copy the updated X config file to ' . $xconfig_file .
          "\n\n");
    # Here temp files are not removed because user may manually copy files
    # to right place.
    return 0;
  }
  if ($addXconfToDb == 1) {
    db_add_file($xconfig_file, 0x0);
  }
  unlink $XF86tmp;
  unlink $xLogFile;
  return 1;
}


# Set blessed file list to automatically start vmware-user
sub configure_autostart {
  my $name = "$gRegistryDir/xautostart.conf";
  my %patch;

  if (not file_name_exist($name)) {
    undef %patch;
    install_file(db_get_answer('LIBDIR') . '/configurator/xautostart.conf',
                 $name, \%patch, 0x1);
    safe_chmod(0644, $name);
  }
}


# Configuration of bridged networking
sub configure_bridged_net {
  my $vHubNr = shift;
  my $vHostIf = shift;
  my $answer;

  if ($vHubNr < $gMinVmnet || $vHubNr > $gMaxVmnet) {
    print wrap('Number of virtual networks exceeded.  Not creating virtual '
               . 'network.' . "\n\n", 0);
    return;
  }

  # If this wasn't a bridged network before, wipe out the old configuration
  # info as it may confuse us later.
  if (!is_bridged_network($vHubNr)) {
    remove_net($vHubNr, $vHostIf);
  }

  print wrap('Configuring a bridged network for vmnet' . $vHubNr . '.'
             . "\n\n", 0);

  if (count_all_networks() == 0 && $#gAllEthIf == -1) {
    # No interface.  We provide a valid default so that everything works.
    make_bridged_net($vHubNr, $vHostIf, "eth0");
    return;
  }

  if ($#gAvailEthIf == 0) {
    # Only one interface.  Use it.  This gives no choice even when the editor
    # is being used.
    make_bridged_net($vHubNr, $vHostIf,  $gAvailEthIf[0]);
    return;
  }

  if ($#gAvailEthIf == -1) {
    # We have other interfaces, but they have all been allocated.
    if (get_answer('All your ethernet interfaces are already bridged.  Are '
                   . 'you sure you want to configure a bridged ethernet '
                   . 'interface for vmnet' . $vHubNr . '? (yes/no)',
                   'yesno', 'no') eq 'no') {
      print wrap('Not changing network settings for vmnet' . $vHubNr . '.'
                 . "\n\n", 0);
      return;
    }
    $answer = get_persistent_answer('Your computer has the following ethernet '
                                    . 'devices: ' . join(', ', @gAllEthIf)
                                    . '. Which one do you want to bridge to '
                                    . 'vmnet' . $vHubNr . '?',
                                    'VNET_' . $vHubNr . '_INTERFACE',
                                    'anyethif', 'eth0');
    make_bridged_net($vHubNr, $vHostIf, $answer);
    return;
  }

  my $queryString = 'Your computer has multiple ethernet network interfaces '
                    . 'available: ' . join(', ', @gAvailEthIf) . '. Which one '
                    . 'do you want to bridge to vmnet' . $vHubNr . '?';
  $answer = get_persistent_answer($queryString,
                                  'VNET_' . $vHubNr . '_INTERFACE',
                                  'availethif', 'eth0');
  make_bridged_net($vHubNr, $vHostIf, $answer);
}

# Creates a bridged network.
sub make_bridged_net {
  my $vHubNr = shift;
  my $vHostIf = shift;
  my $ethIf = shift;

  db_add_answer('VNET_' . $vHubNr . '_INTERFACE', $ethIf);
  configure_dev('/dev/' . $vHostIf, 119, $vHubNr, 1);

  # Reload the list of available ethernet adapters
  load_ethif_info();
}

# Probe for an unused private subnet
# Return value is (status, subnet, netmask).
#  status is 1 on success (subnet and netmask are set),
#  status is 0 on failure.
sub subnet_probe {
  my $vHubNr = shift;
  my $vHostIf = shift;
  # Ref to an array of used subnets
  my $usedSubnets = shift;
  my $i;
  my @subnets;
  my $tries;
  my $maxTries = 100;
  my $pings;
  my $maxPings = 10;
  # XXX We only consider class C subnets for the moment
  my $netmask = '255.255.255.0';
  my %used_subnets;

  # Generate the table of private class C subnets
  @subnets = ();
  for ($i = 0; $i < 255; $i++) {
    $subnets[2 * $i    ] = '192.168.' . $i . '.0';
    $subnets[2 * $i + 1] = '172.16.'  . $i . '.0';
  }

  # Generate a list of used subnets and clear out the ones that have already
  # been used
  foreach $i (@$usedSubnets) {
    $used_subnets{$i} = 1;
  }
  for ($i = 0; $i < $#subnets + 1; $i++) {
    if ($used_subnets{$subnets[$i]}) {
      $subnets[$i] = '';
    }
  }

  print wrap('Probing for an unused private subnet (this can take some '
             . 'time)...' . "\n\n", 0);
  $tries = 0;
  $pings = 0;
  srand(time);
  # Beware, 'last' doesn't seem to work in 'do'-'while' loops
  for (;;) {
    my $r;
    my $subnet;
    my $status;

    $tries++;

    $r = int(rand($#subnets + 1));
    if ($subnets[$r] eq '') {
      # Already tried
      if ($tries == $maxTries) {
        print STDERR wrap('We were unable to locate an unused Class C subnet '
                          . 'in the range of private network numbers.  For '
                          . 'each subnet that we tried we received a response '
                          . 'to our ICMP ping packets from a ' . $machine
                          . ' at the network address intended for assignment '
                          . 'to this machine.  Because no private subnet '
                          . 'appears to be unused you will need to explicitly '
                          . 'specify a network number by hand.' . "\n\n", 0);
        return (0, undef, undef);
      }
      next;
    }
    $subnet = $subnets[$r];
    $subnets[$r] = '';

    # Do a broadcast ping for <subnet>.255 .
    $status = system(shell_string(db_get_answer('BINDIR') . '/vmware-ping')
                     . ' -q ' . ' -b '
                     . shell_string(int_to_quaddot(quaddot_to_int($subnet)
                                                   + 255))) >> 8;

    if ($status == 1) {
      # Some OSes are configured to ignore broadcast ping,
      # so we ping <subnet>.1 .
      $status = system(shell_string(db_get_answer('BINDIR') . '/vmware-ping')
                       . ' -q '
                       . shell_string(int_to_quaddot(quaddot_to_int($subnet)
                                                   + 1))) >> 8;
      if ($status == 1) {
        print wrap('The subnet ' . $subnet . '/' . $netmask . ' appears to be '
                   . 'unused.' . "\n\n", 0);
        return (1, $subnet, $netmask);
      }
    }

    if ($status == 3) {
      print STDERR wrap('We were unable to locate an unused Class C subnet in '
                        . 'the range of private network numbers.  You will '
                        . 'need to explicitly specify a network number by '
                        . 'hand.' . "\n\n", 0);
      return (0, undef, undef);
    }

    if ($status == 2) {
      print STDERR wrap('Either your ' . $machine . ' is not connected to an '
                        . 'IP network, or its network configuration does not '
                        . 'specify a default IP route.  Consequently, the '
                        . 'subnet ' . $subnet . '/' . $netmask . ' appears to '
                        . 'be unused.' . "\n\n", 0);
      return (1, $subnet, $netmask);
    }

    $pings++;
    if (($pings == $maxPings) || ($tries == $maxTries)) {
      print STDERR wrap('We were unable to locate an unused Class C subnet in '
                        . 'the range of private network numbers.  For each '
                        . 'subnet that we tried we received a response to our '
                        . 'ICMP ping packets from a ' . $machine . ' at the '
                        . 'network address intended for assignment to this '
                        . 'machine.  Because no private subnet appears to be '
                        . 'unused you will need to explicitly specify a '
                        . 'network number by hand.' . "\n\n", 0);
      return (0, undef, undef);
    }
  }
}

# Converts an quad-dotted IPv4 address into a integer
sub quaddot_to_int {
  my $quaddot = shift;
  my @quaddot_a;
  my $int;
  my $i;

  @quaddot_a = split(/\./, $quaddot);
  $int = 0;
  for ($i = 0; $i < 4; $i++) {
    $int <<= 8;
    $int |= $quaddot_a[$i];
  }

  return $int;
}

# Converts an integer into a quad-dotted IPv4 address
sub int_to_quaddot {
  my $int = shift;
  my @quaddot_a;
  my $i;

  for ($i = 3; $i >= 0; $i--) {
    $quaddot_a[$i] = $int & 0xFF;
    $int >>= 8;
  }

  return join('.', @quaddot_a);
}

# Compute the subnet address associated to a couple IP/netmask
sub compute_subnet {
  my $ip = shift;
  my $netmask = shift;

  return int_to_quaddot(quaddot_to_int($ip) & quaddot_to_int($netmask));
}

# Compute the broadcast address associated to a couple IP/netmask
sub compute_broadcast {
  my $ip = shift;
  my $netmask = shift;

  return   int_to_quaddot(quaddot_to_int($ip)
         | (0xFFFFFFFF - quaddot_to_int($netmask)));
}

# Makes the patch hash that is used to replace the options in the dhcpd config
# file.
# These DHCP options are needed for the hostonly network.
sub make_dhcpd_patch {
  my $vHubNr = shift;
  my $vHostIf = shift;
  my %patch;

  undef %patch;
  $patch{'%vmnet%'} = $vHostIf;
  $patch{'%hostaddr%'} = db_get_answer('VNET_' . $vHubNr
                                       . '_HOSTONLY_HOSTADDR');
  $patch{'%netmask%'} = db_get_answer('VNET_' . $vHubNr . '_HOSTONLY_NETMASK');
  $patch{'%network%'} = compute_subnet($patch{'%hostaddr%'},
                                       $patch{'%netmask%'});
  $patch{'%broadcast%'} = compute_broadcast($patch{'%hostaddr%'},
                                            $patch{'%netmask%'});
  # Median address in this subnet
  $patch{'%range_low%'} = int_to_quaddot(
    (quaddot_to_int($patch{'%network%'})
     + quaddot_to_int($patch{'%broadcast%'}) + 1) / 2);
  # Last normal address in this subnet
  $patch{'%range_high%'} = int_to_quaddot(
    quaddot_to_int($patch{'%broadcast%'}) - 1);
  $patch{'%router_option%'} = "";
  return %patch;
}

# Write VMware's DHCPd configuration files
sub write_dhcpd_config {
  my $vHubNr = shift;
  my $vHostIf = shift;
  # Function that makes the patch needed for the DHCP config file
  my $make_patch_func = shift;
  my $dhcpd_dir;
  my %patch;

  %patch = &$make_patch_func($vHubNr, $vHostIf);

  # Create the dhcpd config directory (one per virtual interface)
  $dhcpd_dir = $gRegistryDir . '/' . $vHostIf . '/dhcpd';
  create_dir($dhcpd_dir, 0x1);

  install_file(db_get_answer('LIBDIR') . '/configurator/vmnet-dhcpd.conf',
               $dhcpd_dir . '/dhcpd.conf', \%patch, 0x1);

  # Create empty files that will be created by the daemon
  # They will be modified by the daemon, don't timestamp them
  undef %patch;
  install_file('/dev/null', $dhcpd_dir . '/dhcpd.leases', \%patch, 0);
  safe_chmod(0644, $dhcpd_dir . '/dhcpd.leases');
  undef %patch;
  install_file('/dev/null', $dhcpd_dir . '/dhcpd.leases~', \%patch, 0);
  safe_chmod(0644, $dhcpd_dir . '/dhcpd.leases~');
}

# Check the normal dhcp configuration and give advises
sub dhcpd_consultant {
  my $vHubNr = shift;
  my $vHostIf = shift;
  my $conf;
  my $network;
  my $netmask;

  if (-r '/etc/dhcpd.conf') {
    $conf = '/etc/dhcpd.conf';
  } else {
    return;
  }

  $netmask = db_get_answer('VNET_' . $vHubNr . '_HOSTONLY_NETMASK');
  $network = compute_subnet(db_get_answer('VNET_' . $vHubNr
                                          . '_HOSTONLY_HOSTADDR'), $netmask);

  # The host has a normal dhcpd setup
  if (direct_command(
    shell_string($gHelper{'grep'}) . ' '
    . shell_string('^[ ' . "\t" . ']*subnet[ ' . "\t" . ']*' . $network) . ' '
    . shell_string($conf)) eq '') {
    query('This system appears to have a DHCP server configured for normal '
          . 'use.  Beware that you should teach it how not to interfere with '
          . vmware_product_name() . '\'s DHCP server.  There are two ways to '
          . 'do this:' . "\n\n" . '1) Modify the file ' . $conf . ' to add '
          . 'something like:' . "\n\n" . 'subnet ' . $network . ' netmask '
          . $netmask . ' {' . "\n" . '    # Note: No range is given, '
          . 'vmnet-dhcpd will deal with this subnet.' . "\n" . '}' . "\n\n"
          . '2) Start your DHCP server with an explicit list of network '
          . 'interfaces to deal with (leaving out ' . $vHostIf . '). e.g.:'
          . "\n\n" . 'dhcpd eth0' . "\n\n" . 'Consult the dhcpd(8) and '
          . 'dhcpd.conf(5) manual pages for details.' . "\n\n"
          . 'Hit enter to continue.', '', 0);
  }
}

# Configuration of hostonly networking
sub configure_hostonly_net {
  my $vHubNr = shift;
  my $vHostIf = shift;
  my $run_dhcpd = shift;
  my $hostaddr;
  my $subnet;
  my $netmask;
  my $status;

  if ($vHubNr < $gMinVmnet || $vHubNr > $gMaxVmnet) {
    print wrap('Number of virtual networks exceeded.  Not creating virtual '
               . 'network.' . "\n\n", 0);
    return;
  }

  # If this wasn't a hostonly network before, wipe out the old configuration
  # info as it may confuse us later.
  if (!is_hostonly_network($vHubNr)) {
    remove_net($vHubNr, $vHostIf);
  }

  print wrap('Configuring a host-only network for vmnet' . $vHubNr . '.'
             . "\n\n", 0);

  my $keep_settings;

  $keep_settings = 'no';
  $hostaddr = $gDBAnswer{'VNET_' . $vHubNr . '_HOSTONLY_HOSTADDR'};
  $netmask = $gDBAnswer{'VNET_' . $vHubNr . '_HOSTONLY_NETMASK'};

  if (defined($hostaddr) && defined($netmask)) {
    $subnet = compute_subnet($hostaddr, $netmask);
    $keep_settings = get_answer('The host-only network is currently '
                                . 'configured to use the private subnet '
                                . $subnet . '/' . $netmask . '.  Do you want '
                                . 'to keep these settings?', 'yesno', 'yes');
  }

  if ($keep_settings eq 'no') {
    # Get the new settings
    for (;;) {
      my $answer;

      $answer = get_answer('Do you want this program to probe for an unused '
                           . 'private subnet? (yes/no/help)',
                           'yesnohelp', 'yes');

      if ($answer eq 'yes') {
        my @usedSubnets = get_used_subnets();
        ($status, $subnet, $netmask) = subnet_probe($vHubNr, $vHostIf,
                                                    \@usedSubnets);
        if ($status) {
          last;
        }
        # Fallback
        $answer = 'no';
      }

      if ($answer eq 'no') {
	do {
	  $hostaddr = get_answer('What will be the IP address of '
				 . 'your ' . $machine . ' on the '
				 . 'private network?',
				 'ip', '');
	  $netmask = get_answer('What will be the netmask of your '
				. 'private network?',
				'ip', '');
        } until (is_good_network($hostaddr, $netmask) eq 'yes');
	$subnet = compute_subnet($hostaddr, $netmask);
	last;
      }

      print wrap('Virtual machines configured to use host-only networking are '
                 . 'placed on a virtual network that is confined to this '
                 . $machine . '.  Virtual machines on this network can '
                 . 'communicate with each other and the ' . $os . ', but no '
                 . 'one else.' . "\n\n" . 'To setup this host-only networking '
                 . 'you need to select a network number that is normally '
                 . 'unreachable from the ' . $machine . '.  We can '
                 . 'automatically select this number for you, or you can '
                 . 'specify a network number that you want.' . "\n\n" . 'The '
                 . 'automatic selection process works by testing a series of '
                 . 'Class C subnet numbers to see if they are reachable from '
                 . 'the ' . $machine . '.  The first one that is unreachable '
                 . 'is used.  The subnet numbers are chosen from the private '
                 . 'network numbers specified by the Internet Engineering '
                 . 'Task Force (IETF) in RFC 1918 (http://www.isi.edu/in-notes'
                 . '/rfc1918.txt).' . "\n\n" . 'Remember that the host-only '
                 . 'network that virtual machines reside on will not be '
                 . 'accessible outside the host machine.  This means that it '
                 . 'is OK to use the same number on different systems so long '
                 . 'as you do not enable communication between these networks.'
                 . "\n\n", 0);
    }
  }

  make_hostonly_net($vHubNr, $vHostIf, $subnet, $netmask, $run_dhcpd);

  if ($run_dhcpd) {
    dhcpd_consultant($vHubNr, $vHostIf);
  }
}

# Creates a hostonly network
sub make_hostonly_net {
  my $vHubNr = shift;
  my $vHostIf = shift;
  my $subnet = shift;
  my $netmask = shift;
  my $run_dhcpd = shift;

  my $hostaddr = int_to_quaddot(quaddot_to_int($subnet) + 1);

  configure_dev('/dev/' . $vHostIf, 119, $vHubNr, 1);

  db_add_answer('VNET_' . $vHubNr . '_HOSTONLY_HOSTADDR', $hostaddr);
  db_add_answer('VNET_' . $vHubNr . '_HOSTONLY_NETMASK', $netmask);

  if ($run_dhcpd) {
    write_dhcpd_config($vHubNr, $vHostIf, \&make_dhcpd_patch);
  } else {
    # XXX NOT IMPLEMENTED
  }

  # Unmake Samba just in case they have it from a previous product version
  if (defined($gDBAnswer{'NETWORKING'}) && get_samba_net() != -1) {
    unmake_samba_net($vHubNr, $vHostIf);
  }
}

# Get the list of subnets used by all the hostonly networks
sub get_hostonly_subnets {
  my $vHubNr;
  my @subnets = ();
  for ($vHubNr = $gMinVmnet; $vHubNr <= $gMaxVmnet; $vHubNr++) {
    if (is_hostonly_network($vHubNr)) {
      my $hostaddr = db_get_answer('VNET_' . $vHubNr  . '_HOSTONLY_HOSTADDR');
      my $netmask = db_get_answer('VNET_' . $vHubNr  . '_HOSTONLY_NETMASK');
      push(@subnets, compute_subnet($hostaddr, $netmask));
    }
  }
  return @subnets;
}

# Unconfigures Samba from the hostonly network
sub unmake_samba_net {
  my $vHubNr = shift;
  my $vHostIf = shift;
  my $smb_dir = $gRegistryDir . '/' . $vHostIf . '/smb';
  if (is_samba_running($vHubNr)) {
    db_remove_answer('VNET_' . $vHubNr . '_SAMBA');
    db_remove_answer('VNET_' . $vHubNr . '_SAMBA_MACHINESID');
    db_remove_answer('VNET_' . $vHubNr . '_SAMBA_SMBPASSWD');
    uninstall_prefix($smb_dir);
  }
  db_add_answer('VNET_' . $vHubNr . '_SAMBA', 'no');
}

# Gets the virtual network number where Samba is located.
sub get_samba_net {
  my $vHubNr;

  for ($vHubNr = $gMinVmnet; $vHubNr <= $gMaxVmnet; $vHubNr++) {
    if (is_samba_running($vHubNr)) {
      return $vHubNr;
    }
  }

  return -1;
}

# Check to see if the Samba question was ever asked and answered.
# Returns 1 if it has. 0 otherwise.
sub was_samba_answered {
  my $vHubNr;

  for ($vHubNr = $gMinVmnet; $vHubNr <= $gMaxVmnet; $vHubNr++) {
    if (defined($gDBAnswer{'VNET_' . $vHubNr . '_SAMBA'})) {
      return 1;
    }
  }
  return 0;
}

# Configuration of NAT networking
sub configure_nat_net {
  my $vHubNr = shift;
  my $vHostIf = shift;
  my $hostaddr;
  my $subnet;
  my $netmask;
  my $status;

  if ($vHubNr < $gMinVmnet || $vHubNr > $gMaxVmnet) {
    print wrap('Number of virtual networks exceeded.  Not creating virtual '
               . 'network.' . "\n\n", 0);
    return;
  }

  # If this wasn't a NAT network before, wipe out the old configuration info
  # as it may confuse us later.
  if (!is_nat_network($vHubNr)) {
    remove_net($vHubNr, $vHostIf);
  }

  print wrap('Configuring a NAT network for vmnet' . "$vHubNr." . "\n\n", 0);

  my $keep_settings;

  $keep_settings = 'no';
  $hostaddr = $gDBAnswer{'VNET_' . $vHubNr . '_HOSTONLY_HOSTADDR'};
  $netmask = $gDBAnswer{'VNET_' . $vHubNr . '_HOSTONLY_NETMASK'};

  if (defined($hostaddr) && defined($netmask)) {
    $subnet = compute_subnet($hostaddr, $netmask);
    $keep_settings = get_answer('The NAT network is currently configured to '
                                . 'use the private subnet ' . $subnet . '/'
                                . $netmask . '.  Do you want to keep these '
                                . 'settings?', 'yesno', 'yes');
  }

  if ($keep_settings eq 'no') {
    # Get the new settings
    for (;;) {
      my $answer;

      $answer = get_answer('Do you want this program to probe for an unused '
                           . 'private subnet? (yes/no/help)',
                           'yesnohelp', 'yes');

      if ($answer eq 'yes') {
        my @usedSubnets = get_used_subnets();
        ($status, $subnet, $netmask) = subnet_probe($vHubNr, $vHostIf,
                                                    \@usedSubnets);
        if ($status) {
          last;
        }
        # Fallback
        $answer = 'no';
      }

      if ($answer eq 'no') {
	do {
	  $hostaddr = get_answer('What will be the IP address of '
				 . 'your ' . $machine . ' on the '
				 . 'private network?',
				 'ip', '');
	  $netmask = get_answer('What will be the netmask of your '
				. 'private network?',
				'ip', '');
        } until (is_good_network($hostaddr, $netmask) eq 'yes');
	$subnet = compute_subnet($hostaddr, $netmask);
	last;
      }

      print wrap('Virtual machines configured to use NAT networking are '
                 . 'placed on a virtual network that is confined to this '
                 . $machine . '.  Virtual machines on this network can '
                 . 'communicate with the network through the NAT process, '
                 . 'with each other, and with the ' . $os . '.' . "\n\n"
                 . 'To setup NAT networking you need to select a network '
                 . 'number that is normally unreachable from the ' . $machine
                 . '.  We can automatically select this number for you, or '
                 . 'you can specify a network number that you want.' . "\n\n"
                 . 'The automatic selection process works by testing a series '
                 . 'of Class C subnet numbers to see if they are reachable '
                 . 'from the ' . $machine . '.  The first one that is '
                 . 'unreachable is used.  The subnet numbers are chosen from '
                 . 'the private network numbers specified by the Internet '
                 . 'Engineering Task Force (IETF) in RFC 1918 (http://www.isi'
                 . '.edu/in-notes/rfc1918.txt).' . "\n\n" . 'Virtual machines '
                 . 'residing on the NAT network will appear as the host when '
                 . 'accessing the network.  These virtual machines on the NAT '
                 . 'network will not be accessible from outside the host '
                 . 'machine.  This means that it is OK to use the same number '
                 . 'on different systems so long as you do not enable IP '
                 . 'forwarding on the ' . $machine . '.' . "\n\n", 0);
    }
  }

  make_nat_net($vHubNr, $vHostIf, $subnet, $netmask);
  dhcpd_consultant($vHubNr, $vHostIf);
}

# Creates a NAT network
sub make_nat_net {
  my $vHubNr = shift;
  my $vHostIf = shift;
  my $subnet = shift;
  my $netmask = shift;

  my $hostaddr = int_to_quaddot(quaddot_to_int($subnet) + 1);
  my $nataddr = int_to_quaddot(quaddot_to_int($subnet) + 2);

  configure_dev('/dev/' . $vHostIf, 119, $vHubNr, 1);

  db_add_answer('VNET_' . $vHubNr . '_NAT', 'yes');
  db_add_answer('VNET_' . $vHubNr . '_HOSTONLY_HOSTADDR', $hostaddr);
  db_add_answer('VNET_' . $vHubNr . '_HOSTONLY_NETMASK', $netmask);

  write_dhcpd_config($vHubNr, $vHostIf, \&make_nat_patch);
  write_nat_config($vHubNr, $vHostIf);
}

# Write NAT configuration files
sub write_nat_config {
  my $vHubNr = shift;
  my $vHostIf = shift;
  my $nat_dir;
  my %patch;

  # Create the nat config directory (one per virtual interface)
  $nat_dir = $gRegistryDir . '/' . $vHostIf . '/nat';
  create_dir($nat_dir, 0x1);

  undef %patch;

  my $hostaddr = db_get_answer('VNET_' . $vHubNr . '_HOSTONLY_HOSTADDR');
  my $netmask = db_get_answer('VNET_' . $vHubNr . '_HOSTONLY_NETMASK');
  my $network = compute_subnet($hostaddr, $netmask);
  my $broadcast = compute_broadcast($hostaddr, $netmask);
  my $nataddr = int_to_quaddot(quaddot_to_int(compute_subnet($hostaddr,
                                                             $netmask)) + 2);

  $patch{'%nataddr%'} = $nataddr;
  $patch{'%netmask%'} = $netmask;
  $patch{'%sample%'} = int_to_quaddot(
    (quaddot_to_int($network) + quaddot_to_int($broadcast) + 1) / 2);
  $patch{'%vmnet%'} = "/dev/" . $vHostIf;
  install_file(db_get_answer('LIBDIR') . '/configurator/vmnet-nat.conf',
               $nat_dir . '/nat.conf', \%patch, 0x1);
}

# Makes the patch hash that is used to replace the options in the dhcpd config
# file.
# These DHCP options are needed for the NAT network.
sub make_nat_patch {
  my $vHubNr = shift;
  my $vHostIf = shift;
  my %patch;

  my $hostaddr = db_get_answer('VNET_' . $vHubNr . '_HOSTONLY_HOSTADDR');
  my $netmask = db_get_answer('VNET_' . $vHubNr . '_HOSTONLY_NETMASK');
  my $nataddr = int_to_quaddot(quaddot_to_int(compute_subnet($hostaddr,
                                                             $netmask)) + 2);

  undef %patch;
  $patch{'%vmnet%'} = $vHostIf;
  $patch{'%hostaddr%'} = $nataddr;
  $patch{'%netmask%'} = $netmask;
  $patch{'%network%'} = compute_subnet($nataddr, $netmask);
  $patch{'%broadcast%'} = compute_broadcast($nataddr, $netmask);
  # Median address in this subnet
  $patch{'%range_low%'} = int_to_quaddot(
    (quaddot_to_int($patch{'%network%'})
     + quaddot_to_int($patch{'%broadcast%'}) + 1) / 2);
  # Last normal address in this subnet
  $patch{'%range_high%'} = int_to_quaddot(quaddot_to_int($patch{'%broadcast%'})
                                          - 1);
  $patch{'%router_option%'} = "option routers $nataddr;";
  return %patch;
}

# Get the list of subnets used by all the nat networks
sub get_nat_subnets {
  my $vHubNr;
  my @subnets = ();
  for ($vHubNr = $gMinVmnet; $vHubNr <= $gMaxVmnet; $vHubNr++) {
    if (is_nat_network($vHubNr)) {
      my $hostaddr = db_get_answer('VNET_' . $vHubNr  . '_HOSTONLY_HOSTADDR');
      my $netmask = db_get_answer('VNET_' . $vHubNr  . '_HOSTONLY_NETMASK');
      push(@subnets, compute_subnet($hostaddr, $netmask));
    }
  }
  return @subnets;
}

# Get the list of subnets that are already used by virtual networks
sub get_used_subnets {
  return (&get_hostonly_subnets(), &get_nat_subnets());
}

# Return the specific VMware product
sub vmware_product {
  return 'vserver';
}

# This is a function in case a future product name contains language-specific
# escape characters.
sub vmware_product_name {
  return 'VMware Server';
}

# Returns the name of the main binary for this install.
sub vmware_binary {
  return 'vmware';
}

sub vmware_tools_app_name {
  return db_get_answer('BINDIR') . '/vmware-toolbox';
}

#
# check to see if the certificate files exist (and
# that they appear to be a valid certificate).
#
sub certificateExists {
  my $certLoc = shift;
  my $openssl_exe = shift;
  my $certPrefix = shift;
  return ((-e "$certLoc/$certPrefix.crt") &&
          (-e "$certLoc/$certPrefix.key") &&
          !(system(shell_string("$openssl_exe") . ' x509 -in'
                   . shell_string("$certLoc") . "/$certPrefix.crt " .
                   ' -noout -subject > /dev/null 2>&1')));
}

# Helper function to create SSL certificates
sub createSSLCertificates {
  my ($openssl_exe, $vmware_version, $certLoc, $certPrefix, $unitName) = @_;
  my $certUniqIdent = "(564d7761726520496e632e)";
  my $certCnf;
  my $curTime = time();
  my $hostname = direct_command(shell_string($gHelper{"hostname"}));

  my $cTmpDirPrefix = "vmware-ssl-config";
  my $tmpdir;

  if (certificateExists($certLoc, $openssl_exe, $certPrefix)) {
    print wrap("Using Existing SSL Certificate.\n", 0);
    return;
  }

  # Create the directory
  if (! -e $certLoc) {
    create_dir($certLoc, 0x1);
  }

  $tmpdir = make_tmp_dir($cTmpDirPrefix);
  $certCnf = "$tmpdir/certificate.cnf";
  if (not open(CONF, '>' . $certCnf)) {
    error('Couldnt open "' . "$certCnf" . '".' . "\n"
          . 'Unable to create SSL Certificate. You must run '
          . '"security-config.pl -n" by hand.' . "\n");
  }
  print CONF <<EOF;
  # Conf file that we will use to generate SSL certificates.

[ req ]
default_bits		= 1024
default_keyfile 	= $certPrefix.key
distinguished_name	= req_distinguished_name

#Don't encrypt the key
encrypt_key             = no
prompt                  = no

string_mask = nombstr

[ req_distinguished_name ]
countryName= US
stateOrProvinceName     = California

localityName            = Palo Alto

0.organizationName      = VMware, Inc.

organizationalUnitName  = $unitName

commonName              = $hostname

unstructuredName        = ($curTime),$certUniqIdent

emailAddress            = ssl-certificates\@vmware.com
EOF
  close(CONF);

  print wrap("Generating SSL Server Certificate\n\n", 0);
  system(shell_string("$openssl_exe") . ' req -new -x509 -keyout '
         . shell_string("$certLoc") . '/' . shell_string("$certPrefix")
         . '.key -out ' . shell_string("$certLoc") . '/'
         . shell_string("$certPrefix") . '.crt -config '
         . shell_string("$certCnf") . ' -days 5000 > /dev/null 2>&1');
  db_add_file("$certLoc/$certPrefix.key", 0x1);
  db_add_file("$certLoc/$certPrefix.crt", 0x1);

  remove_tmp_dir($tmpdir);
  # Make key readable only by root (important)
  # We've seen unreliable behavior by perl's built-in chmod() for these files,
  # so we'll fall back to the more reliable system chmod for these critical
  # cases, _and_ check the return value!
  sys_chmod( '0400', shell_string("$certLoc") . '/'
	 . shell_string("$certPrefix") . '.key');

  # Let anyone read the certificate
  sys_chmod( '0444', shell_string("$certLoc") . '/'
	 . shell_string("$certPrefix") . '.crt');
}

# Security configuration:  Add certificates for the remote console.
sub configure_security() {
  my $version;
  if (vmware_product() eq 'server') {
     $version = 'ESX';
  } else {
     $version = 'GSX';
  }

  createSSLCertificates(db_get_answer('LIBDIR') . '/bin/openssl',
                        $version,
                        $gRegistryDir . '/ssl',
                        'rui',
                        'VMware Management Interface');
}

# Configuration related to the specific features of the Workgroup Server (GSX)
# product and VMware Server
sub configure_wgs {
  my $program;

  foreach $program ('killall', 'tar', 'perl', 'make', 'rm', 'cp', 'mv',
                    'touch', 'hostname') {
    if (not defined($gHelper{$program})) {
      $gHelper{$program} = DoesBinaryExist_Prompt($program);
      if ($gHelper{$program} eq '') {
        error('Unable to continue.' . "\n\n");
      }
    }
  }


  # Create the /var/log/vmware directory for event logs
  create_dir('/var/log/vmware', 0x1);

  # Kill any running vmware-serverd process.
  system(shell_string($gHelper{'killall'}) . ' -TERM vmware-serverd '
         . '>/dev/null 2>&1');

  configure_wgs_superserver();
  configure_wgs_perl();
  if (vmware_product() ne 'server') {
    # authd pam file is automatically installed in ESX Server
    configure_wgs_pam_d();
  }
  fix_vmlist_permissions();
}

# Try to find a free port for authd use starting from default passed in
# If none are available, return default passed in
sub get_port_for_authd {
  my $base_port = shift;
  my $port = $base_port;
  my $max_range = 65536;
  while (check_answer_authdport($port, "default") ne $port) {
    $port = ($port + 1) % $max_range;
    if ($base_port == $port) {
      last;
    }
  }
  return $port;
}

# Try and figure out which "superserver" is installed and update to correct
# one.
sub configure_wgs_superserver {
  my $inetd_conf  = "/etc/inetd.conf";
  my $xinetd_conf = "/etc/xinetd.conf";
  my $xinetd_dir  = "/etc/xinetd.d";
  my $success     = 0;
  my $port;

  if (defined(db_get_answer_if_exists("AUTHDPORT"))) {
    $port = db_get_answer_if_exists("AUTHDPORT");
  } else {
    # We'll try to find a good default port that is free
    $port = get_port_for_authd($gDefaultAuthdPort);
    if ($port != $gDefaultAuthdPort) {
      print wrap('The default port : '. $gDefaultAuthdPort. ' is not free.'
                 . ' We have selected a suitable alternative port for '
                 . vmware_product_name()
                 . ' use. You may override this value now.' . "\n", 0);
      print wrap(' Remember to use this port when connecting to this server.'
                 . "\n", 0);
    }
  }
  $port = get_persistent_answer('Please specify a port for remote console'
                                . ' connections to use',
                                'AUTHDPORT',
                                'authdport',
                                $port);

  if ($gDefaultAuthdPort != $port) {
    print wrap('WARNING: ' . vmware_product_name(). ' has been configured to '
               . 'run on a port different from the default port. '
               . 'Remember to use this port when connecting to this server.'
               . "\n", 0);
  }

  # check for xinetd
  # XXX Could be a problem, as they could start xinetd with '-f config_file'.
  #     We could do a ps -ax, look for xinetd, parse the line, find the config
  #     file, parse the config file to find the xinet.d directory.  Bah.  Or
  #     parse if from the init.d script somewhere.  If they use init.d.
  if (-e $xinetd_conf) {
    if (open(CONF, $xinetd_conf)) {
        # Let's try to find it here
        while (<CONF>) {
          if (/^\s*includedir\s*(\S+)\s*$/) {
            $xinetd_dir = $1;
            last;
          }
        }
        close(CONF);
      }
      if (-d $xinetd_dir) {
        configure_wgs_xinetd($xinetd_conf, $xinetd_dir, $port);
        $success = 1;
      } else {
        print wrap('WARNING: An xinetd.conf exists but we couldnt find the '
                   . 'directory xinetd uses to store config files. '
                   . 'Please reinstall or reconfigure the xinetd package'
                   . ' and re-run this configuration program'
                   . "\n", 0);
      }
  }

  if (!$success) {
    # check for inetd
    if (-e $inetd_conf) {
      configure_wgs_inetd($inetd_conf, $port);
      $success = 1;
    }
  }

  if ($success) {
    return;
  }

  query('Unable to find any instance of the super-server "inetd" or '
        . '"xinetd".  It is possible that you do not have one of these '
        . 'packages installed on this machine.  Please install "inetd" or '
        . '"xinetd".' . "\n\n" . 'If you do have "inetd" or "xinetd" '
        . 'installed, make sure that ' . $inetd_conf . ' or ' . $xinetd_dir
        . ' exists.' . "\n" . 'The configuration will continue, but you '
        . 'should re-run ' . $0 . ' after you fix the super-server.' . "\n\n"
        . 'Hit enter to continue.', '', 0);
  exit 1;
}


# Restart the inetd service
sub restart_inetd {
  my $inetd_restart = db_get_answer('INITSCRIPTSDIR') . '/inetd';
  if (-e $inetd_restart) {
    if (!system(shell_string($inetd_restart) . ' restart')) {
      return;
    }
  }

  if (system(shell_string($gHelper{'killall'}) . ' -HUP inetd')) {
    query('Unable to make the Internet super-server (inetd) re-read its '
          . 'configuration file.  Please restart inetd by hand:' . "\n"
          . '    killall -v -HUP inetd' . "\n\n"
          . 'Hit enter to continue.', '', 0);
  }
}

# Cleanup the inetd.conf file.
sub uninstall_inetd {
  my $inetd = shift;
  my %patch = ('^# VMware auth.*$' => '',
          '^.*stream\s+tcp\s+nowait.*vmauthd.*$' => '',
          '^.*stream\s+tcp\s+nowait.*vmware-authd.*$' => '');
  my $tmp_dir = make_tmp_dir('vmware-installer');
  # Build the temp file's path
  my $tmp = $tmp_dir . '/inetd.' . $$;

  internal_sed($inetd, $tmp, 0, \%patch);
  undef %patch;

  if (not internal_sed($tmp, $inetd, 0, \%patch)) {
    query('Unable to copy file ' . $tmp . ' back to ' . $inetd
          . '.' . "\n" . 'The authentication daemon was not '
          . 'removed from ' . $inetd . "\n\n"
          . 'Hit enter to continue', 0);
  }
  remove_tmp_dir($tmp_dir);

}

# Update the Internet super-server's configuration file, and make the
# super-server read it
sub configure_wgs_inetd {
  # XXX Use the block_*() API instead, like we do for $cServices. --hpreg
  my $conf_file = shift;
  my $port      = shift;
  my $authd;

  $authd = db_get_answer('SBINDIR') . "/vmware-authd";

  # First check if our port number is in use in /etc/services
  my $success = check_port_not_registered($port);
  if ($success == -1) {
    query('Unable to read the "' . $cServices
          . '" file.  Consequently, this program cannot check for the presence of "'
          . $authd . '" in the file.  You will have to do it by hand before running '
          . vmware_product_name() . '.' . "\n\n" . 'Hit enter to continue.', '', 0);
    return;
  }

  if ($success == 0) {
    query('You already have a service running on port "' . $port . '" in the "'
          . $cServices . '" file.  No change will be made to it.' . "\n\n"
          . ' You will have to pick a new port, less than 1024,'
          . ' for vmware-authd to use.' . "\n\n" . 'Hit enter to continue.'
          , '', 0);
    return;
  }


  # Open the inetd.conf file and check if our entry is already there.
  if (not open(CONF, $conf_file)) {
    query('Unable to read the "' . $conf_file . '" file.  Consequently, this '
          . 'program cannot check for the presence of "' . $authd . '" in the '
          . 'file.  You will have to do it by hand before running '
          . vmware_product_name() . '.' . "\n\n" . 'Hit enter to continue.',
          '', 0);
    return;
  }

  while (<CONF>) {
    if (/^$port.*stream.*tcp.*nowait.*vmware-authd$/i) {
      query('You already have an entry for "' . $authd . '" in the "'
            . $conf_file . '" file.  No change will be made to it.' . "\n\n"
            . 'Hit enter to continue.', '', 0);
      close(CONF);
      return;
    }
  }
  close(CONF);
  uninstall_inetd($conf_file);

  if (not open(CONF, '>>' . $conf_file)) {
    query('Unable to append to the "' . $conf_file . '"file.  Consequently, '
          . 'this program cannot add a "' . $authd . '" entry in the file.  '
          . 'You will have to do it by hand before running '
          . vmware_product_name() . '.' . "\n\n" . 'Hit enter to continue.',
          '', 0);
    return;
  }

  print CONF '# VMware authentification daemon' . "\n" . $port
             . ' stream tcp nowait root ' . $authd . ' vmware-authd' . "\n";
  close(CONF);
  restart_inetd();
}

#Restart xinetd
sub restart_xinetd {
  my $xinetd_restart = db_get_answer('INITSCRIPTSDIR') . '/xinetd';
  if (-e $xinetd_restart) {
    if (!system(shell_string($xinetd_restart) . ' restart')) {
      return;
    }
  }
  if (system(shell_string($gHelper{'killall'}) . ' -USR2 xinetd')) {
    query('Unable to make the Internet super-server (xinetd) re-read its '
          . 'configuration file.  Please restart xinetd by hand:' . "\n"
          . '    killall -v -USR2 xinetd' . "\n\n"
          . 'Hit enter to continue.', '', 0);
  }
}

# Update the Internet super-server's configuration file, and make the
# super-server read it
sub configure_wgs_xinetd {
  my $conf_file = shift;
  my $conf_dir  = shift;
  my $port      = shift;

  my $authd_conf_file = "$conf_dir/vmware-authd";
  my $authd = db_get_answer('SBINDIR') . "/vmware-authd";

  # Create the new vmware-authd file
  # XXX This file should be registered with the installer's database. --hpreg
  if (not open(CONF, '>' . $authd_conf_file)) {
    query('Unable to create the "' . $authd_conf_file . '"file.  '
          . 'Consequently, this program cannot add a "' . $authd . '" entry '
          . 'in the file.  You will have to do it by hand before running '
          . vmware_product_name() . '.' .  "\n\n" . 'Hit enter to continue.',
          '', 0);
    return;
  }
  print CONF <<END;
# default: on
# description: The VMware remote access authentification daemon
service vmware-authd
{
    disable         = no
    port            = $port
    socket_type     = stream
    protocol        = tcp
    wait            = no
    user            = root
    server          = $authd
    type            = unlisted
}
END
  close CONF;

  # Make sure the IP service is registered, as RH 9.0's xinetd is picky about
  # that (was bug 26864). --hpreg
  if (check_port_not_registered($port) == 1) {
    block_append($cServices, $cMarkerBegin,
                 'vmware-authd ' . $port . '/tcp' . "\n", $cMarkerEnd);
  }

  restart_xinetd();
}

# Handle the installation and configuration of vmware's perl module
# WARNING: This code is highly duplicated from build_perl_api in pkg_mgr.pl
sub configure_wgs_perl {
  my $control;
  my $build_dir;

  print wrap('Configuring the VMware VmPerl Scripting API.' . "\n", 0);

  $control = db_get_answer('LIBDIR') . '/perl/control.tar';
  if (not (-e $control)) {
    error('Unable to find the VMware VmPerl Scripting API.  You may want to '
          . 're-install ' . vmware_product_name() . '.' .  "\n\n");
  }

  $build_dir = make_tmp_dir($cTmpDirPrefix);

  if (system(shell_string($gHelper{'tar'}) . ' -C ' . shell_string($build_dir)
             . ' -xopf ' . shell_string($control))) {
    error('Unable to untar the "' . $control . '" file in the "'
          . $build_dir . '" directory.' . "\n\n");
  }

  if (system('cd ' . shell_string($build_dir . '/control-only') . ' && '
             . shell_string($gHelper{'perl'})
             . ' Makefile.PL > make.log 2>&1')) {
    print wrap('Unable to create the VMware VmPerl Scripting API makefile.'
               . "\n\n", 0);
    return perl_config_fail($build_dir);
  }

  # Look for the header files needed to build the Perl module.  If we don't
  # find them, suggest to the user how they can install the files. -jhu
  if (open(PERLINC, shell_string($gHelper{'perl'}) . ' -MExtUtils::Embed ' .
           '-e perl_inc |')) {
    my $inc = <PERLINC>;
    close(PERLINC);
    $inc =~ s/\s*-I//;
    $inc =~ s/\s*$//;
    if ((! -e $inc . '/perl.h') || (! -e $inc . '/EXTERN.h') ||
	     (! -e $inc . '/XSUB.h')) {
      print wrap('Could not find necessary components to build the '
                 . 'VMware VmPerl Scripting API.  Look in your Linux '
                 . 'distribution to see if there is a perl-devel package.  '
                 . 'Install that package if it exists and then re-run this '
                 . 'installation program.' . "\n\n", 0);
      return perl_config_fail($build_dir);
    }
  } else {
      print wrap('Could not get the perl include path. Please be sure your '
		 . 'perl installation is complete.' . "\n\n", 0);
      return perl_config_fail($build_dir);
  }

  print "\n";

  print wrap('Building the VMware VmPerl Scripting API.' . "\n\n", 0);

  # Make sure we have a compiler available
  if (get_cc() eq '') {
    print wrap('Unable to install the VMware VmPerl Scripting API.', 0);
    print wrap('A C compiler is required to install the API.' . "\n\n",  0);
    if ($gSystem{'distribution'} eq 'suse') {
      # SUSE SLES 8.0 doesnt install the gcc rpm by default
      print wrap('Please make sure to install the gcc rpm from your SUSE installation CD' .
                 ' and rerun this program.' .
                 "\n\n", 0);
    }
    remove_tmp_dir($build_dir);
    return;
  }

  # We touch all our files in case the system clock is set to the past.  Make will get confused and
  # delete our shipped .o file(s).
  system(shell_string($gHelper{'touch'}) . ' '
         . shell_string($build_dir . '/control-only') . '/* >>'
         . shell_string($build_dir . '/control-only') . '/make.log 2>&1');

  if (system(shell_string($gHelper{'make'}) . ' -C '
             . shell_string($build_dir . '/control-only') . ' '
             . shell_string('CC=' . $gHelper{'gcc'}) . ' '
             . ' >>' . shell_string($build_dir . '/control-only') . '/make.log 2>&1')) {
    print wrap('Unable to compile the VMware VmPerl Scripting API.' . "\n\n", 0);
    return(perl_config_fail($build_dir));
  }

  print wrap("Installing the VMware VmPerl Scripting API.\n\n", 0);


  # XXX This is deeply broken: we let a third party tool install a file without
  #     adding it to our installer database.  This file will never get
  #     uninstalled by our uninstaller --hpreg
  if (system(shell_string($gHelper{'make'}) . ' -C '
             . shell_string($build_dir . '/control-only') . ' '
             . shell_string('CC=' . $gHelper{'gcc'}) . ' '
             . ' install >>' . shell_string($build_dir . '/control-only')
             . '/make.log 2>&1')) {
    print wrap('Unable to install the VMware VmPerl Scripting API.' . "\n\n", 0);
    return(perl_config_fail($build_dir));
  }

  print wrap('The installation of the VMware VmPerl Scripting API succeeded.' . "\n\n", 0);
  remove_tmp_dir($build_dir);
}

#  Setup the init.pl file that serverd uses
sub configure_serverd {
  my %patch;

  $patch{'%libdir%'} = db_get_answer('LIBDIR');
  install_file(db_get_answer('LIBDIR') . '/serverd/init.pl.default',
               db_get_answer('LIBDIR') . '/serverd/init.pl', \%patch, 0x1);
}

#  Move the /etc/vmware/pam.d information to its real home in /etc/pam.d
sub configure_wgs_pam_d {
  my %patch;
  my $target = '/etc/pam.d/vmware-authd';
  my $template = $gRegistryDir . '/pam.d/vmware-authd';

  my $libpam = '/lib/libpam.so.0';  # Look only at standard location
  my $libdir = db_get_answer('LIBDIR');
  my $pamdir = $libdir . '/lib/libpam.so.0/security';

  if (-e $libpam and not is64BitElf($libpam)) {
    $pamdir = '/lib/security';
  }
  $patch{'%pamdir%'} = $pamdir;
  install_file($template, $target, \%patch, 0x1);
}

# both configuration.
sub show_net_config {
  my $bridge_flag = shift;
  my $hostonly_flag = shift;
  my $nat_flag = shift;

  # Don't show anything
  if (!$hostonly_flag && !$bridge_flag && !$nat_flag) {
    return;
  }

  # Print a message describing what we are showing
  my $nettype = 'virtual';
  if (!$bridge_flag && !$nat_flag && $hostonly_flag) {
    $nettype = 'host-only';
  } elsif (!$hostonly_flag && !$nat_flag && $bridge_flag) {
    $nettype = 'bridged';
  } elsif (!$bridge_flag && !$hostonly_flag && $nat_flag) {
    $nettype = 'NAT';
  }
  print wrap('The following ' . $nettype . ' networks have been defined:'
             . "\n\n", 0);

  # Number of networks configured
  my $count = 0;

  local(*WFD);
  # Don't show networking configuration in --default case because the pager
  # from gHelper{'more'} might require user input. See bug 99796.
  if ($gOption{'default'} != 1) {
    if (not open(WFD, '| ' . $gHelper{'more'})) {
      error("Could not print networking configuration.\n");
    }
  }

  my $i;
  for ($i = $gMinVmnet; $i <= $gMaxVmnet; $i++) {
    if ($bridge_flag && is_bridged_network($i)) {
    my $bridge = $gDBAnswer{'VNET_' . $i . '_INTERFACE'};
      print WFD wrap(". vmnet" . $i . ' is bridged to ' . $bridge . "\n", 0);
      $count++;
    } elsif ($hostonly_flag && is_hostonly_network($i)) {
      my $hostonly_addr = $gDBAnswer{'VNET_' . $i . '_HOSTONLY_HOSTADDR'};
      my $hostonly_mask = $gDBAnswer{'VNET_' . $i . '_HOSTONLY_NETMASK'};
      my $sambaInfo = '';
      if (is_samba_running($i)) {
        $sambaInfo = '  This network had a Samba server running to allow '
                     . 'virtual machines to share the ' . $os . '\'s '
                     . 'filesystem. This is now obsolete. Please use the '
                     . 'VMware shared folders feature.';
      }

      print WFD wrap(". vmnet" . $i . ' is a host-only network on private '
                     . 'subnet '
                     . compute_subnet($hostonly_addr, $hostonly_mask) . '.'
                     . $sambaInfo . "\n", 0);
      $count++;
    } elsif ($nat_flag && is_nat_network($i)) {
      my $hostonly_addr = $gDBAnswer{'VNET_' . $i . '_HOSTONLY_HOSTADDR'};
      my $hostonly_mask = $gDBAnswer{'VNET_' . $i . '_HOSTONLY_NETMASK'};
      print WFD wrap(". vmnet" . $i . ' is a NAT network on private subnet '
                     . compute_subnet($hostonly_addr, $hostonly_mask) . '.'
                     . "\n", 0);
      $count++;
    }
  }

  if ($count == 0) {
    print WFD wrap(". No virtual networks configured.\n", 0);
  }

  print WFD wrap("\n", 0);

  close(WFD);
}

# Unconfigures the now obsolete Samba networking
sub unconfigure_samba {
  print wrap('Removing obsolete VMware Samba config info. To access the ' .
             'host filesystem please use the VMware shared folders.' .
             "\n\n", 0);
  unmake_samba_net($gDefHostOnly, 'vmnet' . $gDefHostOnly);
  return;
}

# Go through the /etc/vmware/vm-list file and set permissions correctly
#  also, upgrade vmkernel device names on ESX Server
sub fix_vmlist_permissions {
  my $file = '/etc/vmware/vm-list';
  my $cf;

  if (not -e $file) {
    return;
  }

  if (get_answer('Do you want this program to set up permissions for your '
                 . 'registered virtual machines?  This will be done by '
                 . 'setting new permissions on all files found in the "'
                 . $file . '" file.', 'yesno', 'no') eq 'no') {
    return;
  }

  if (not open(F, "$file")) {
    print wrap('Aborting attempt to change permissions on config files found '
               . 'in "' . $file . '": Cannot read the file.' . "\n\n", 0);
    return;
  }
  while (<F>) {
    s/"//g;
    # This comment fixes emacs's broken syntax highlighting"
    ($cf) = m/^config (.*)$/;
    if (!defined($cf) || (not -e $cf) || (not -f $cf)) {
      next;
    }
    if (chmod(0754, $cf) != 1) {
      print wrap('Cannot change permissions on file "' . $cf . '".' . "\n\n",
                 0);
    }
  }
  close(F);
}

# Check the system requirements to install this product
sub check_wgs_memory {
  my $availableRAMInMB;
  my $minRAMinMB = 256;

  $availableRAMInMB = memory_get_total_ram();
  if (not defined($availableRAMInMB)) {
    if (get_persistent_answer('Unable to determine the total amount of memory '
                              . 'on this system.  You need at least '
                              . $minRAMinMB . ' MB.  Do you really want to '
                              . 'continue?',
                              'PASS_RAM_CHECK', 'yesno', 'no') eq 'no') {
      exit(0);
    }
  } elsif ($availableRAMInMB < $minRAMinMB) {
    if (get_persistent_answer('There are only ' . $availableRAMInMB . ' MB '
                              . 'of memory on this system.  You need at least '
                              . $minRAMinMB . ' MB.  Do you really want to '
                              . 'continue?',
                              'PASS_RAM_CHECK', 'yesno', 'no') eq 'no') {
      exit(0);
    }
  }
}


# Retrieve the amount of RAM (in MB)
# Return undef if unable to determine
sub memory_get_total_ram {
  my $line;
  my $availableRAMInMB = undef;

  if (not open(MEMINFO, '</proc/meminfo')) {
    error('Unable to read the "/proc/meminfo" file.' . "\n\n");
  }
  while (defined($line = <MEMINFO>)) {
    chomp($line);

    if ($line =~ /^Mem:\s*(\d+)/) {
      $availableRAMInMB = $1 / (1024 * 1024);
      last;
    }
    if ($line =~ /^MemTotal:\s*(\d+)\s*kB/) {
      $availableRAMInMB = $1 / 1024;
      last;
    }
  }
  if (defined($availableRAMInMB)) {
    #
    # Round up total memory to the nearest multiple of 8 or 32 MB, since the
    # "total" amount of memory reported by Linux is the total physical memory
    # minus the amount used by the kernel
    #

    if ($availableRAMInMB < 128) {
      $availableRAMInMB = CEILDIV($availableRAMInMB, 8) * 8;
    } else {
      $availableRAMInMB = CEILDIV($availableRAMInMB, 32) * 32;
    }
  }
  close(MEMINFO);

  return $availableRAMInMB;
}

sub CEILDIV {
  my $left = shift;
  my $right = shift;

  return int(($left + $right - 1) / $right);
}


# Common error message when we can't compile or install our perl modules
sub perl_config_fail {
  my $dir = shift;

  print wrap('********' . "\n". 'The VMware VmPerl Scripting API was not '
             . 'installed.  Errors encountered during compilation and '
             . 'installation of the module can be found here: ' . $dir
             . "\n\n" . 'You will not be able to use the "vmware-cmd" '
             . 'program.' . "\n\n" . 'Errors can be found in the log file: '
             . shell_string($dir . '/control-only/make.log')
             . "\n" . '********' . "\n\n", 0);
  query('Hit enter to continue.', '', 0);
}

sub build_vmnet {
  if (db_get_answer('NETWORKING') ne 'no') {
    if (configure_module('vmnet') eq 'no') {
      module_error();
    }
  }
}

# Configuration related to networking
sub configure_net {
  my $i;

  # Fix for bug 15842.  Always regenerate the network settings because an
  # upgrade leaves us in an inconsistent state.  The database will have
  # the network settings, but the necessary configuration files such as
  # dhcpd.conf will not exist until we run make_all_net(). -jhu
  make_all_net();

  if (defined($gDBAnswer{'NETWORKING'}) && count_all_networks() > 0) {
    print wrap('You have already setup networking.' . "\n\n", 0);
    if (get_persistent_answer('Would you like to skip networking setup and '
                              . 'keep your old settings as they are? (yes/no)',
                              'NETWORKING_SKIP_SETUP', 'yesno', 'yes')
                              eq 'yes') {
      return;
    }
  }

  for (;;) {
    my $answer;
    my $helpString;
    my $default;
    my $prompt = 'Do you want networking for your virtual machines? '
               . '(yes/no/help)';
    $default = 'yes';
    $helpString = 'Networking will allow your virtual machines to use a '
                  . 'virtual network. There are primarily two types of '
                  . 'networking available: bridged and host-only.  A '
                  . 'bridged network is a virtual network that is '
                  . 'connected to an existing ethernet device.  With a '
                  . 'bridged network, your virtual machines will be able '
                  . 'to communicate with other machines on the network to '
                  . 'which the ethernet card is attached.  A host-only '
                  . 'network is a private network between your virtual '
                  . 'machines and ' . $os . '.  Virtual machines connected '
                  . 'to a host-only network may only communicate directly '
                  . 'with other virtual machines or the ' . $os
                  . '.  A virtual machine may be '
                  . 'configured with more than one bridged or host-only '
                  . 'network.' . "\n\n" . 'If you want your virtual '
                  . 'machines to be connected to a network, say "yes" '
                  . 'here.' . "\n\n";

    $answer = get_persistent_answer($prompt, 'NETWORKING', 'yesnohelp',
                                    $default);
    if (($answer eq 'no') || ($answer eq 'yes')) {
      last;
    }

    print wrap($helpString, 0);
  }

  if (db_get_answer('NETWORKING') eq 'no') {
    # Turning off networking turns off hostonly.
    remove_all_networks(1, 1, 1);
    return;
  }

  for ($i = 0; $i < $gNumVmnet; $i++) {
    configure_dev('/dev/vmnet' . $i, 119, $i, 1);
  }

  # If there is a previous network configuration, prompt the user to
  # see if the user would like to modify the existing configuration.
  # If the user chooses to modify the settings, give the choice of
  # either the wizard or the editor.
  #
  # If there is no previous network configuration, use the wizard.
  if (count_all_networks() > 0) {
    for (;;) {
      my $answer;
      $answer = get_persistent_answer('Would you prefer to modify your '
                                      . 'existing networking configuration '
                                      . 'using the wizard or the editor? '
                                      . '(wizard/editor/help)',
                                      'NETWORKING_EDITOR', 'editorwizardhelp',
                                      'wizard');
      if (($answer eq 'editor') || ($answer eq 'wizard')) {
        last;
      }

      print wrap('The wizard will present a series of questions that will '
                 . 'help you quickly add new virtual networks.  However, you '
                 . 'cannot remove networks or edit existing networks with the '
                 . 'wizard.  To remove or edit existing networks, you should '
                 . 'use the editor.' . "\n\n", 0);
    }

    if (db_get_answer('NETWORKING_EDITOR') eq 'editor') {
      configure_net_editor();
      return;
    }
  }
  configure_net_wizard();
}

# Network configuration wizard
sub configure_net_wizard() {
  my $answer;

  # Bridged Networking
  if (db_get_answer('NETWORKING') eq 'yes' && count_bridged_networks() == 0) {
    # Make a default one unless it exists already
    configure_bridged_net($gDefBridged, 'vmnet' . $gDefBridged);
  }

  show_net_config(1, 0, 0);
  while ($#gAvailEthIf > -1) {
    if (get_answer('Do you wish to configure another bridged network? '
                   . '(yes/no)', 'yesno', 'no') eq 'no') {
      last;
    }
    my $free = get_free_network();
    configure_bridged_net($free, 'vmnet' . $free);
    show_net_config(1, 0, 0);
  }
  if ($#gAvailEthIf == -1) {
    print wrap ('All your ethernet interfaces are already bridged.'
		. "\n\n", 0);
  }

  # NAT networking
  $answer = get_answer('Do you want to be able to use NAT networking '
                       . 'in your virtual machines? (yes/no)', 'yesno', 'yes');

  if ($answer eq 'yes') {
    configure_nat_net($gDefNat, 'vmnet' . $gDefNat);
  } elsif ($answer  eq 'no') {
    remove_all_networks(0, 0, 1);
  }

  if ($answer eq 'yes') {
    while (1) {
      show_net_config(0, 0, 1);
      if (get_answer('Do you wish to configure another NAT network? '
                     . '(yes/no)', 'yesno', 'no') eq 'no') {
        last;
      }
      my $free = get_free_network();
      configure_nat_net($free, 'vmnet' . $free);
    }
  }

  # Host only networking
  $answer = get_answer('Do you want to be able to use host-only networking '
                       . 'in your virtual machines?', 'yesno', $answer);

  if ($answer eq 'yes') {
    configure_hostonly_net($gDefHostOnly, 'vmnet' . $gDefHostOnly, 1);
  } elsif ($answer  eq 'no') {
    remove_all_networks(0, 1, 0);
  }

  if ($answer eq 'yes') {
    while (1) {
      show_net_config(0, 1, 0);
      if (get_answer('Do you wish to configure another host-only network? '
                     . '(yes/no)', 'yesno', 'no') eq 'no') {
        last;
      }
      my $free = get_free_network();
      configure_hostonly_net($free, 'vmnet' . $free, 1);
    }
  }
}

# Network configuration editor
sub configure_net_editor() {
  my $answer = 'yes';
  my $first_time = 1;
  while ($answer ne 'no') {
    show_net_config(1, 1, 1);

    if (!$first_time) {
      $answer =
        get_persistent_answer('Do you wish to make additional changes to the '
                              . 'current virtual networks settings? (yes/no)',
                              'NETWORK_EDITOR_CHANGE', 'yesno', 'no');
    } else {
      $answer =
        get_persistent_answer('Do you wish to make any changes to the current '
                              . 'virtual networks settings? (yes/no)',
                              'NETWORK_EDITOR_CHANGE', 'yesno', 'no');
      $first_time = 0;
    }
    if ($answer eq 'no') {
      last;
    }

    my $vHubNr = get_answer('Which virtual network do you wish to configure? '
                            . '(' . $gMinVmnet . '-' . $gMaxVmnet . ')',
                            'vmnet', '');

    if ($vHubNr == $gDefBridged) {
      if (get_answer('The network vmnet' . $vHubNr . ' has been reserved for '
                     . 'a bridged network.  You may change it, but it is '
                     . 'highly recommended that you use it as a bridged '
                     . 'network.  Are you sure you want to modify it? '
                     . '(yes/no)', 'yesno', 'no') eq 'no') {
        next;
      }
    }

    if ($vHubNr == $gDefHostOnly) {
      if (get_answer('The network vmnet' . $vHubNr . ' has been reserved for '
                     . 'a host-only network.  You may change it, but it is '
                     . 'highly recommended that you use it as a host-only '
                     . 'network.  Are you sure you want to modify it? '
                     . '(yes/no)', 'yesno', 'no') eq 'no') {
        next;
      }
    }

    if ($vHubNr == $gDefNat) {
      if (get_answer('The network vmnet' . $vHubNr . ' has been reserved for '
                     . 'a NAT network.  You may change it, but it is highly '
                     . 'recommended that you use it as a NAT network.  Are '
                     . 'you sure you want to modify it? (yes/no)',
                     'yesno', 'no') eq 'no') {
        next;
      }
    }

    my $nettype = 'none';
    if (is_bridged_network($vHubNr)) {
      $nettype = 'bridged';
    } elsif (is_hostonly_network($vHubNr)) {
      $nettype = 'hostonly';
    } elsif (is_nat_network($vHubNr)) {
      $nettype = 'nat';
    }
    $answer = get_answer('What type of virtual network do you wish to set '
                         . 'vmnet' . $vHubNr . '? (bridged,hostonly,nat,none)',
                         'nettype', $nettype);

    if ($answer eq 'bridged') {
      # Special case: if we are changing a bridge network to another
      # bridge network, we need to make the interface that it used to
      # be defined as the correct one again.
      if (is_bridged_network($vHubNr)) {
        add_ethif_info(db_get_answer('VNET_' . $vHubNr . '_INTERFACE'));
      }
      configure_bridged_net($vHubNr, 'vmnet' . $vHubNr);
      # Reload available ethernet info in case user does make a change
      load_ethif_info();
    } elsif ($answer eq 'hostonly') {
      configure_hostonly_net($vHubNr, 'vmnet' . $vHubNr, 1);
    } elsif ($answer eq 'nat') {
      configure_nat_net($vHubNr, 'vmnet' . $vHubNr);
    } elsif ($answer eq 'none') {
      remove_net($vHubNr, 'vmnet' . $vHubNr);
    }
  }
}

# Configure networking automatically with no input from the user, keeping the
# existing settings.
sub make_all_net() {
  my $vHubNr;
  for ($vHubNr = $gMinVmnet; $vHubNr <= $gMaxVmnet; $vHubNr++) {
    if (is_bridged_network($vHubNr)) {
      my $ethIf = db_get_answer('VNET_' . $vHubNr . '_INTERFACE');
      make_bridged_net($vHubNr, 'vmnet' . $vHubNr, $ethIf);
    } elsif (is_hostonly_network($vHubNr)) {
      my $hostaddr = db_get_answer('VNET_' . $vHubNr . '_HOSTONLY_HOSTADDR');
      my $netmask = db_get_answer('VNET_' . $vHubNr . '_HOSTONLY_NETMASK');
      my $subnet = compute_subnet($hostaddr, $netmask);
      make_hostonly_net($vHubNr, 'vmnet' . $vHubNr, $subnet, $netmask, 1);
    } elsif (is_nat_network($vHubNr)) {
      my $hostaddr = db_get_answer('VNET_' . $vHubNr . '_HOSTONLY_HOSTADDR');
      my $netmask = db_get_answer('VNET_' . $vHubNr . '_HOSTONLY_NETMASK');
      my $subnet = compute_subnet($hostaddr, $netmask);
      make_nat_net($vHubNr, 'vmnet' . $vHubNr, $subnet, $netmask);
    }
  }
}

# Counts the number of bridged networks
sub count_bridged_networks {
  return count_networks(1, 0, 0, 0);
}

# Counts the number of hostonly networks
sub count_hostonly_networks {
  return count_networks(0, 1, 0, 0);
}

# Counts the number of hostonly networks running samba
sub count_samba_networks {
  return count_networks(0, 1, 0, 1);
}

# Counts the number of hostonly networks running NAT
sub count_nat_networks {
  return count_networks(0, 0, 1, 0);
}

# Counts the number of configured virtual networks
sub count_all_networks {
  return count_networks(1, 1, 1, 0);
}

# Counts the number of virtual networks that have been setup.
# bridged: Set to indicate a desire to count the number of bridged networks
# hostonly: Set to indicate a desire to count the number of hostonly networks
# nat: Set to indicate a desire to count the number of nat networks
# samba: Set to indicate a desire to count the number of hostonly networks
#        running Samba.
sub count_networks {
  my $bridged = shift;
  my $hostonly = shift;
  my $nat = shift;
  my $samba = shift;

  my $i;
  my $count = 0;
  for ($i = $gMinVmnet; $i <= $gMaxVmnet; $i++) {
    if (is_bridged_network($i) && $bridged) {
      $count++;
    } elsif (is_hostonly_network($i) && $hostonly) {
      if ($samba && is_samba_running($i)) {
        $count++;
      } elsif (!$samba) {
        $count++;
      }
    } elsif (is_nat_network($i) && $nat) {
      $count++;
    }
  }

  return $count;
}

# Indicates if a virtual network has been defined on this virtual net
sub is_network {
  my $vHubNr = shift;

  return    is_bridged_network($vHubNr)
         || is_hostonly_network($vHubNr)
         || is_nat_network($vHubNr);
}

# Indicates if a bridged virtual network is defined for a particular vnet
sub is_bridged_network {
  my $vHubNr = shift;
  my $bridged_ethIf = $gDBAnswer{'VNET_' . $vHubNr . '_INTERFACE'};

  return defined($bridged_ethIf);
}

# Indicates if a hostonly virtual network is defined for a particular vnet
sub is_hostonly_network {
  my $vHubNr = shift;
  my $hostonly_hostaddr = $gDBAnswer{'VNET_' . $vHubNr . '_HOSTONLY_HOSTADDR'};
  my $hostonly_netmask = $gDBAnswer{'VNET_' . $vHubNr . '_HOSTONLY_NETMASK'};
  my $nat_network = $gDBAnswer{'VNET_' . $vHubNr . '_NAT'};

  return    defined($hostonly_hostaddr)
         && defined($hostonly_netmask)
         && not (defined($nat_network) && $nat_network eq 'yes');
}

# Indicates if a NAT virtual network is defined for a particular vnet
sub is_nat_network {
  my $vHubNr = shift;
  my $nat_hostaddr = $gDBAnswer{'VNET_' . $vHubNr . '_HOSTONLY_HOSTADDR'};
  my $nat_netmask = $gDBAnswer{'VNET_' . $vHubNr . '_HOSTONLY_NETMASK'};
  my $nat_network = $gDBAnswer{'VNET_' . $vHubNr . '_NAT'};

  return    defined($nat_hostaddr)
         && defined($nat_netmask)
         && defined($nat_network) && $nat_network eq 'yes';
}

# Indicates if the given network collides with an existing network
# (and if the user is amenable to this)
sub is_good_network {
  my $new_hostaddr = shift;
  my $new_netmask = shift;
  my $new_subnet = compute_subnet($new_hostaddr, $new_netmask);
  my $new_broadcast = compute_broadcast($new_hostaddr, $new_netmask);
  my $vHubNr;

  # Get all networks
  # We can't use get_used_subnets because we want the broadcast address
  # for each subnet as well.
  my @networks = ();
  for ($vHubNr = $gMinVmnet; $vHubNr <= $gMaxVmnet; $vHubNr++) {
    my $hostaddr =
      db_get_answer_if_exists('VNET_' . $vHubNr . '_HOSTONLY_HOSTADDR');
    my $netmask =
      db_get_answer_if_exists('VNET_' . $vHubNr . '_HOSTONLY_NETMASK');
    if (not $hostaddr or not $netmask) {
      next;
    }
    my $subnet = compute_subnet($hostaddr, $netmask);
    my $broadcast = compute_broadcast($hostaddr, $netmask);

    # Check for collisions
    # Each network is defined by a range from subnet (low-end) to
    # broadcast (high-end). Collisions occur when the two ranges overlap.
    if (quaddot_to_int($new_subnet) <= quaddot_to_int($broadcast) &&
        quaddot_to_int($new_broadcast) >= quaddot_to_int($subnet)) {
      push(@networks, 'vmnet' . $vHubNr);
    }
  }

  if (scalar(@networks) != 0) {
    return get_answer(sprintf('The new private network has collided with '
			      . 'existing private %s %s. Are you sure you '
			      . 'wish to add it?', scalar(@networks) == 1 ?
			      'network' : 'networks', join(', ', @networks)),
		      'yesno', 'no');
  }
  return 'yes';
}

# Indicates if samba is running on a virtual network
sub is_samba_running {
  my $vHubNr = shift;
  my $hostonly = is_hostonly_network($vHubNr);
  my $samba = $gDBAnswer{'VNET_' . $vHubNr . '_SAMBA'};

  return    $hostonly
         && defined($samba) && $samba eq 'yes';
}

# Gets a free virtual network number.  Gets the lowest number available.
# Returns -1 on failure.
sub get_free_network {
  my $i;
  for ($i = $gMinVmnet; $i <= $gMaxVmnet; $i++) {
    if (grep($i == $_, @gReservedVmnet)) {
      next;
    }
    if (!is_network($i)) {
      return $i;
    }
  }

  return -1;
}

# Removes a bridged network
sub remove_bridged_network {
  my $vHubNr = shift;
  my $vHostIf = shift;

  if ($vHubNr < $gMinVmnet || $vHubNr > $gMaxVmnet) {
    return;
  }

  print wrap('Removing a bridged network for vmnet' . $vHubNr . '.' . "\n\n",
             0);
  db_remove_answer('VNET_' . $vHubNr . '_INTERFACE');
  if ($vHubNr >= $gNumVmnet) {
    uninstall_file('/dev/' . $vHostIf);
  }

  # Reload the list of available ethernet adapters
  load_ethif_info();
}

# Removes a hostonly network
sub remove_hostonly_network {
  my $vHubNr = shift;
  my $vHostIf = shift;
  my $vmnet_dir = $gRegistryDir . '/' . $vHostIf;

  if ($vHubNr < $gMinVmnet || $vHubNr > $gMaxVmnet) {
    return;
  }

  print wrap('Removing a host-only network for vmnet' . $vHubNr . '.' .
             "\n\n", 0);
  # Remove the samba settings
  unmake_samba_net($vHubNr, $vHostIf);

  db_remove_answer('VNET_' . $vHubNr . '_HOSTONLY_HOSTADDR');
  db_remove_answer('VNET_' . $vHubNr . '_HOSTONLY_NETMASK');
  uninstall_prefix($vmnet_dir);

  if ($vHubNr >= $gNumVmnet) {
    uninstall_file('/dev/' . $vHostIf);
  }
}

# Removes a NAT network
sub remove_nat_network {
  my $vHubNr = shift;
  my $vHostIf = shift;
  my $vmnet_dir = $gRegistryDir . '/' . $vHostIf;

  if ($vHubNr < $gMinVmnet || $vHubNr > $gMaxVmnet) {
    return;
  }

  print wrap('Removing a NAT network for vmnet' . $vHubNr . '.' . "\n\n", 0);

  db_remove_answer('VNET_' . $vHubNr . '_NAT');
  db_remove_answer('VNET_' . $vHubNr . '_HOSTONLY_HOSTADDR');
  db_remove_answer('VNET_' . $vHubNr . '_HOSTONLY_NETMASK');
  uninstall_prefix($vmnet_dir);

  if ($vHubNr >= $gNumVmnet) {
    uninstall_file('/dev/' . $vHostIf);
  }
}

# Removes a network
sub remove_net {
  my $vHubNr = shift;
  my $vHostIf = shift;
  if (is_bridged_network($vHubNr)) {
    remove_bridged_network($vHubNr, $vHostIf);
  } elsif (is_hostonly_network($vHubNr)) {
    remove_hostonly_network($vHubNr, $vHostIf);
  } elsif (is_nat_network($vHubNr)) {
    remove_nat_network($vHubNr, $vHostIf);
  }
}

# Removes all networks on the system subject to the following
# types
sub remove_all_networks {
  my $bridged = shift;
  my $hostonly = shift;
  my $nat = shift;
  my $i;

  for ($i = $gMinVmnet; $i <= $gMaxVmnet; $i++) {
    if (is_network($i)) {
      if ($bridged && is_bridged_network($i)) {
        remove_bridged_network($i, 'vmnet' . $i);
      }
      if ($hostonly && is_hostonly_network($i)) {
        remove_hostonly_network($i, 'vmnet' . $i);
      }
      if ($nat && is_nat_network($i)) {
        remove_nat_network($i, 'vmnet' . $i);
      }
    }
  }
}

# Loads ethernet interface info into global variable
sub load_all_ethif_info() {
  # Get the list of available ethernet interfaces
  # The -a is important because it lists all interfaces (not only those
  # which are up).  The vmnet driver knows how to deal with down interfaces.
  open(IFCONFIG, 'LC_ALL=C ' . shell_string($gHelper{'ifconfig'}) . ' -a |');
  @gAllEthIf = ();
  while (<IFCONFIG>) {
    if (/^(\S+)\s+Link encap:Ethernet/) {
      my @fields;

      @fields = split(/[ ]+/);
      push(@gAllEthIf, $fields[0]);
    }
  }
  close(IFCONFIG);
}

# Determines the available ethernet interfaces
sub load_ethif_info() {
  # Get the list of available ethernet interfaces by checking the all
  # list and removing the ones that have already been allocated.
  @gAvailEthIf = ();

  my @usedEthIf = grep(/^VNET_\d+_INTERFACE$/, keys(%gDBAnswer));
  @usedEthIf = map($gDBAnswer{$_}, @usedEthIf);

  my $eth;
  foreach $eth (@gAllEthIf) {
    if (!grep($_ eq $eth, @usedEthIf)) {
      push(@gAvailEthIf, $eth);
    }
  }
}

# Adds an ethernet interface to the working list of ethernet interfaces
sub add_ethif_info {
  my $eth = shift;
  push(@gAvailEthIf, $eth);
}

# Install a pair of S/K startup scripts for a given runlevel
sub link_runlevel {
   my $level = shift;
   my $service = shift;
   my $S_level = shift;
   my $K_level = shift;

   #
   # Create the S symlink
   #
   install_symlink(db_get_answer('INITSCRIPTSDIR') . '/' . $service,
                   db_get_answer('INITDIR') . '/rc' . $level . '.d/S'
                   . $S_level . $service);

   #
   # Create the K symlink
   #
   install_symlink(db_get_answer('INITSCRIPTSDIR') . '/' . $service,
                   db_get_answer('INITDIR') . '/rc' . $level . '.d/K'
                   . $K_level . $service);
}

# Create the links for VMware's services taking the service name and the
# requested levels
sub link_services {
   my @fields;
   my $service = shift;
   my $S_level = shift;
   my $K_level = shift;

   # Create the links the LSB way when possible
   if ($gHelper{'insserv'} ne '') {
      if (0 == system(shell_string($gHelper{'insserv'}) . ' '
                 . shell_string(db_get_answer('INITSCRIPTSDIR')
                                . '/' . $service))) {
         return;
      }
   }

   # Now try using chkconfig if available.
   # Note: RedHat's chkconfig reads LSB INIT INFO if present.
   if ($gHelper{'chkconfig'} ne '') {
      if (0 == system(shell_string($gHelper{'chkconfig'}) . ' '
                      . $service . ' reset')) {
         return;
      }
   }

   # Set up vmware to start/stop at run levels 2, 3 and 5
   link_runlevel(2, $service, $S_level, $K_level);
   link_runlevel(3, $service, $S_level, $K_level);
   link_runlevel(5, $service, $S_level, $K_level);

   # Set up vmware to stop at run levels 0 and 6
   install_symlink(db_get_answer('INITSCRIPTSDIR') . '/' . $service,
                   db_get_answer('INITDIR') . '/rc0' . '.d/K'
                   . $K_level . $service);
   install_symlink(db_get_answer('INITSCRIPTSDIR') . '/' . $service,
                   db_get_answer('INITDIR') . '/rc6' . '.d/K'
                   . $K_level . $service);
}

# Create the links for VMware's services on a Solaris system
sub link_services_solaris {
   my $service = shift;
   my $S_level = shift;
   my $K_level = shift;
   my @S_runlevels = ('2');
   my @K_runlevels = ('0', '1', 'S');
   my $runlevel;

   foreach $runlevel (@S_runlevels) {
     install_symlink(db_get_answer('INITSCRIPTSDIR') . '/' . $service,
                     db_get_answer('INITDIR') . '/rc' . $runlevel
                     . '.d/S' . $S_level . $service);
   }

   foreach $runlevel (@K_runlevels) {
     install_symlink(db_get_answer('INITSCRIPTSDIR') . '/' . $service,
                     db_get_answer('INITDIR') . '/rc' . $runlevel
                     . '.d/K' . $K_level . $service);
   }
}

# Write the VMware host-wide configuration file
sub write_vmware_config {
  my $name;
  my $backupName;
  my $promoconfig;

  $name = $gRegistryDir . '/config';
  $backupName = $gStateDir . '/config';

  my $config = new VMware::Config;
  # First read in old config backed up from last uninstallation.
  if (file_name_exist($backupName)) {
    if (!$config->readin($backupName)) {
      error('Unable to read configuration file "' . $backupName . '".' . "\n\n");
    }
    db_remove_file($backupName);
  }

  my $bindir = db_get_answer('BINDIR');
  my $libdir = db_get_answer('LIBDIR');

  $config->set('vmware.fullpath', $bindir . '/vmware');
  $config->set('dhcpd.fullpath', $bindir . '/vmnet-dhcpd');
  $config->set('loop.fullpath', $bindir . '/vmware-loop');
  $config->set('control.fullpath', $bindir . '/vmware-cmd');
  $config->set('libdir', $libdir);
  if (vmware_product() eq 'wgs' ||
      vmware_product() eq 'vserver' ||
      vmware_product() eq 'server') {
      $config->set('authd.client.port', db_get_answer('AUTHDPORT'));
  }
  if (vmware_product() eq 'wgs' ||
      vmware_product() eq 'vserver') {
    my $answer;
    $answer = get_persistent_answer('In which directory do you want to keep your '
				    . 'virtual machine files?', 'VMDIR', 'dirpath',
				    '/var/lib/vmware/Virtual Machines');
    create_dir($answer, 0x1);
    $config->set('vmdir', $answer);
    safe_chmod(01777, $answer);
  }
  my $vHubNr;
  for ($vHubNr = $gMinVmnet; $vHubNr <= $gMaxVmnet; $vHubNr++) {
    if (is_hostonly_network($vHubNr)) {
      my $hostaddr = db_get_answer('VNET_' . $vHubNr  . '_HOSTONLY_HOSTADDR');
      my $netmask = db_get_answer('VNET_' . $vHubNr  . '_HOSTONLY_NETMASK');
      # Used by the Linux wizard to determine if a hostonly network is
      # configured.
      # XXX It's misleading to put this information into the config file since
      #     modifying this config option won't actually change the subnet that
      #     the hostonly network is using -jhu
      #     I'm not so sure anymore. I have seen it used --hpreg
      $config->set('vmnet' . $vHubNr . '.HostOnlyAddress', $hostaddr);
      $config->set('vmnet' . $vHubNr . '.HostOnlyNetMask', $netmask);
    } else {
      $config->remove('vmnet' . $vHubNr . '.HostOnlyAddress');
      $config->remove('vmnet' . $vHubNr . '.HostOnlyNetMask');
    }
  }
  # Used by the Linux wizard to determine if Samba is configured on the
  # hostonly network.
  $config->remove('smbpasswd.fullpath');

  if (vmware_product() eq 'wgs' ||
      vmware_product() eq 'vserver' ||
      vmware_product() eq 'server') {
    my $sbindir = db_get_answer('SBINDIR');
    $config->set('authd.fullpath', $sbindir . '/vmware-authd');
    $config->set('serverd.fullpath', $sbindir . '/vmware-serverd');
    $config->set('serverd.init.fullpath', $libdir . '/serverd/init.pl');
  } else {
    $config->remove('authd.fullpath');
    $config->remove('serverd.fullpath');
    $config->remove('serverd.init.fullpath');
  }

  if (!$config->writeout($name)) {
    error('Unable to write configuration file "' . $name . '".' . "\n\n");
  }
  db_add_file($name, 0x1);
  safe_chmod(0644, $name);

  # Append the promotional configuration if it exists
  $promoconfig = $libdir . '/configurator/PROMOCONFIG';
  if (-e $promoconfig) {
    my %patch;

    undef %patch;
    internal_sed($promoconfig, $name, 1, \%patch);
  }
}

# Write the VMware tools configuration file
sub write_tools_config {
  my $name;
  my $backupName;

  $name = $gRegistryDir . '/tools.conf';
  $backupName = $gStateDir . '/tools.conf';

  my $config = new VMware::Config;
  # First read in old config backed up from last uninstallation.
  if (file_name_exist($backupName)) {
    if (!$config->readin($backupName)) {
      error('Unable to read configuration file "' . $backupName . '".' . "\n\n");
    }
    db_remove_file($backupName);
  }

  $config->set('bindir', db_get_answer('BINDIR'));
  if (!$config->writeout($name)) {
    error('Unable to write configuration file "' . $name . '".' . "\n\n");
  }
  db_add_file($name, 0x1);
  safe_chmod(0644, $name);
}

# Display the PROMOCODE information
sub show_PROMOCODE {
  my $promocode;

  $promocode = db_get_answer('DOCDIR') . '/PROMOCODE';
  # Don't show promocode in --default case because the pager
  # from gHelper{'more'} might require user input. See bug 99796.
  if (-e $promocode && $gOption{'default'} != 1) {
    # $gHelper{'more'} is already a shell string
    system($gHelper{'more'} . ' ' . shell_string($promocode));
    print "\n";
  }
}

# If needed, allow the sysadmin to unlock a site wide license. This must be
# called _after_ VMware's config file has been written
sub check_license {
  my $want_sn;
  my $sn;

  if (system(shell_string(vmware_vmx_app_name())
             . ' --can-run')) {
    $want_sn = 'yes';
  } else {
    for (;;) {
      $want_sn = get_answer('Do you want to enter a serial number now? '
                            . '(yes/no/help)', 'yesnohelp', 'no');
      if (not ($want_sn eq 'help')) {
        last;
      }

      print wrap('Answer "yes" if you have received a new serial number. '
                 . 'Otherwise answer "no", and ' . vmware_product_name()
                 . ' will continue to run just fine.' . "\n\n", 0);
    }
  }

  if ($want_sn eq 'yes') {
    $sn = '';
    while ($sn eq '') {
      $sn = get_answer("Please enter your 20-character serial number.\n\n"
		       . "Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel: ",
		       'serialnum', '');
      if ($sn eq ' ') {
	print wrap ('You cannot power on any virtual machines until you enter a '
		    . 'valid serial number. To enter the serial number, run this '
		    . 'configuration program again, or choose '
		    . "'Help > Enter Serial Number' "
		    . 'in the virtual machine console.' . "\n\n", 0);
      } elsif (system(shell_string(vmware_vmx_app_name()) . ' --new-sn ' . $sn) != 0) {
	print wrap('The serial number ' . $sn . ' is invalid.' . "\n\n", 0);
        $sn = '';
      }
    }
  }
}

# Display a usage error message for the configuration program and exit
sub config_usage {
  if ((vmware_product() eq 'mui') || (vmware_product eq 'console')) {
    print STDERR wrap(vmware_longname() . 'configurator' . "\n" .
                      'Usage: ' . $0 . ' [[-][-]d[default]]' . "\n" .
                      'default: Automatically answer questions with the ' .
                      'proposed answer.' . "\n\n", 0);
  } else {
    print STDERR wrap(vmware_longname() . ' configurator' . "\n" . 'Usage: '
                      . $0 . ' [[-][-]d[efault]] [[-][-]c[ompile]] '
                      . '[[-][-]p[rebuilt]]' . ' [[-][-]t[ry-modules]]'
                      . "\n" . '. default: Automatically '
                      . 'answer questions with the proposed answer.' . "\n"
                      . '. compile: Force the compilation of kernel modules.'
                      . "\n" . '. prebuilt: Force the use of pre-built kernel '
                      . 'modules.' . "\n"
                      . '. try-modules: Try to load all the compatible modules '
                      . 'from the ' . vmware_product_name() . ' package.'
                      . "\n\n", 0);
  }
  exit 1;
}

# Return GSX or ESX for server products, Workstation for ws
sub installed_vmware_version {
  my $vmware_version;
  my $vmware_version_string;

  if (not defined($gHelper{"vmware"})) {
    $gHelper{"vmware"} = DoesBinaryExist_Prompt("vmware");
    if ($gHelper{"vmware"} eq '') {
      error('Unable to continue.' . "\n\n");
    }
  }

  $vmware_version_string = direct_command(shell_string($gHelper{"vmware"})
                                          . ' -v 2>&1 < /dev/null');
  if ($vmware_version_string =~ /.*VMware GSX Server.*/) {
    $vmware_version = 'GSX';
  } elsif ($vmware_version_string =~ /.*VMware ESX Server.*/) {
    $vmware_version = 'ESX';
  } elsif ($vmware_version_string =~ /.*VMware Server.*/) {
    $vmware_version = 'vserver';
  } else {
    $vmware_version = "Workstation";
  }
  return $vmware_version;
}

# Stop the old run of the mui during uninstall
sub stop_mui {
  my $installDir = db_get_answer('INSTALLDIR');
  my $initDir = db_get_answer('INITSCRIPTSDIR');
  if (-e "$installDir/apache/bin") {
    system('$initDir/httpd.vmware stop > /dev/null 2>&1');
  }
}

# Start the http process up
sub start_mui {
  my $installDir = db_get_answer('INSTALLDIR');
  my $initDir = db_get_answer('INITSCRIPTSDIR');
  if (-e "$installDir/apache/bin") {
    system("$initDir/httpd.vmware start");
  } else {
    error('Cannot find the Apache instance for this install in : "'
          . shell_string($installDir) . '/apache"' . "\n"
         . 'Failed to start' .  "\n");
  }
  return 0;
}

# Configure the mui
sub configure_mui {
  my $program;
  my @modFiles       = (
                        "apache/conf/httpd.conf",
                        "apache/conf/access.conf",
                        "apache/conf/setup.pl",
                        "apache/bin/apachectl",
                        "apache/bin/apxs",
                        "lib/perl5/site_perl/5.005/VMware/Management/Overview.pm",
                        "lib/perl5/site_perl/5.005/VMware/HConfig/Constant.pm",
                        "lib/httpd.vmware"
                       );
  stop_mui();

  # Find the programs we need to go ahead with the install
  foreach $program ('rm', 'vmware', 'hostname', 'cp', 'mkdir') {
    if (not defined($gHelper{$program})) {
      $gHelper{$program} = DoesBinaryExist_Prompt($program);
      if ($gHelper{$program} eq '') {
        error('Unable to continue.' . "\n\n");
      }
    }
  }

  # Create the /var/log/vmware-mui logs for MUI logs
  create_dir('/var/log/vmware-mui', 0x1);

  # We have to modify the files in the install package to replace place-holders
  # with real values
  updateMuiFiles(\@modFiles);
  # Set the correct user for apache to run as
  findNobody();
  # Create the service links
  updateInitdir();
  # set timeout for httpd
  setTimeout();
  # Recreate SSL certificates
  createSSLCertificates(db_get_answer('INSTALLDIR') . '/bin/openssl',
                        installed_vmware_version(),
                        $gRegistryDir . '/ssl',
                        'mui',
                        'VMware Management Interface');

  # Start your engines
  if (installed_vmware_version() ne 'ESX') {
    if (start_mui()) {
      print wrap("\n" . 'Installation of ' . vmware_product_name()
                 . ' was successful' . "\n\n", 0);
    }
  }
  else {
    my $initDir = db_get_answer('INITSCRIPTSDIR');
    print wrap("\n" . 'Installation of ' . vmware_product_name()
               . " was successful.\nTo start the " . vmware_product_name()
               . ', use ' . $initDir . '/etc/init.d/httpd.vmware start' . "\n\n", 0);
  }
}

# set the timeout for session expiry in our httpd (PR 8636)
sub setTimeout {
  my $installDir = db_get_answer('INSTALLDIR');
  my $accessConf = $installDir . "/apache/conf/access.conf";
  my $accessConfSrc = $installDir . "/src/apache/conf/access.conf";
  my $currentTimeout;
  my $defaultTimeout = 60;
  my $refPatch;

  if (not open(CONF, '<' . $accessConf)) {
    print wrap('Couldnt open "' . $accessConf . '" for reading.'
               . ' Not modifying the default timeout value.' . "\n\n",0);
    return;
  }
  while (<CONF>) {
    if (/^\s*PerlSetEnv\s*vmware_SESSION_LENGTH\s*(\d+)\s*$/) {
      $currentTimeout = $1;
    }
  }
  close(CONF);
  my $newTimeout =
    get_persistent_answer('Set the number of minutes before a http session'
                          . ' times out. (This is the '
                          . 'length of time before someone connecting to '
                          . vmware_product_name() . ' will be logged out)'
                          , 'TIMEOUT', 'timeout'
                          , $defaultTimeout);

  $refPatch = updateMuiFiles();
  $$refPatch{"PerlSetEnv vmware_SESSION_LENGTH $currentTimeout"} =
    "PerlSetEnv vmware_SESSION_LENGTH $newTimeout";
  # install the modified file
  install_file($accessConfSrc, $accessConf, $refPatch, 0x1);
}

#Update the place-holders in the MUI files with installation values
sub updateMuiFiles {
  my $refModFiles = shift;
  my $vmware_version;
  my $inst_dir = db_get_answer('INSTALLDIR');
  my $iter;
  my $srcFile;
  my $destFile;
  my $dir;
  my %patch;

  # Find whether this is an install of gsx/vserver or esx
  $vmware_version = installed_vmware_version();

  my $hostname = direct_command(shell_string($gHelper{"hostname"}));
  chomp($hostname);
  my $portOption = ($vmware_version eq "GSX" || $vmware_version eq "vserver") ?
     "-DGSX" : "-DSTANDARD_PORTS -DESX";

  my $initDir = db_get_answer('INITSCRIPTSDIR');
  undef %patch;
  $patch{"\@\@PREFIX\@\@"} = $inst_dir;
  $patch{"\@\@HOSTNAME\@\@"} = $hostname;
  $patch{"\@\@PORT_OPTION\@\@"} = $portOption;
  $patch{"\@\@INITDIR\@\@"} = $initDir;
  if (defined($refModFiles)) {
    foreach $iter (@$refModFiles) {
      $srcFile = "$inst_dir/src/$iter";
      $destFile = "$inst_dir/$iter";
      # install the modified file
      install_file($srcFile, $destFile, \%patch, 0x1);
    }
  }
  return \%patch;
}

# Find an init dir update with our apache startup info.
sub updateInitdir {
  my $dir;
  my $initDir = "";
  my $initDirRoot = "";
  my $temp_dir;
  my $instDir = db_get_answer('INSTALLDIR');
  my %patch;

  $initDir = db_get_answer('INITDIR');
  $initDirRoot = db_get_answer('INITSCRIPTSDIR');
  undef %patch;
  install_file("$instDir/lib/httpd.vmware", "$initDirRoot/httpd.vmware"
               , \%patch, 0x1);

  link_services("httpd.vmware", "91", "07");

  if (system("chmod 755 $initDirRoot/httpd.vmware")) {
    error(" chmod fails:\n  chmod 755 $initDirRoot/httpd.vmware\n\n");
  }
}

# Find the www/apache/web user & group
sub findNobody {
  my $pw    = "/etc/passwd";
  my $gf    = "/etc/group";
  my @ulist = ("nobody", "wwwrun", "nouser", "www-data", "www");
  my @glist = ("nobody", "nogroup", "www");
  my $user  = undef;
  my $group = undef;
  my $i;
  my $instDir = db_get_answer('INSTALLDIR');

  # Deal with USER
  $user = db_get_answer_if_exists('USER');
  if (not defined $user) {
    foreach $i (@ulist) {
      $user = $i if (not system(shell_string($gHelper{'grep'})
                                . " ^$i"
                                . ": $pw > /dev/null 2>&1"));
    }
  }


  if (not defined $user) {
    print wrap('The installer cant find a username that will run the web server'
               . '. Please enter one now.  Make sure to add this user to '
               . "'$pw'." . ' Be aware the the ' . vmware_product_name()
               . ' web server wont start correctly until you add this user'
               . "\n", 0);
    $user = get_persistent_answer('What is the user under whom you would like'
                                  . ' Apache to run?', 'USER', 'usergp'
                                  , 'nobody');
  } else {
    db_add_answer('USER', $user);
  }

  # Deal with GROUP
  $group = db_get_answer_if_exists('GROUP');
  if (not defined $group) {
    foreach $i (@glist) {
      $group = $i if (not system(shell_string($gHelper{'grep'})
                                 . " ^$i: $gf > /dev/null 2>&1"));
    }
  }

  if (not defined $group) {
    print wrap('The installer cant find a group that will run the web'
               . ' server. Please enter one now.  Make sure to add this'
               . ' group to ' . "$gf" . '. Be aware that the '
               . vmware_product_name() . ' web server wont start correctly'
               . ' until you add this group to ' . "$gf" . "\n", 0);
    $group = get_persistent_answer('What is the group under whom you would like'
                                   . ' Apache ro run?', 'GROUP', 'usergp',
                                   'nobody');
  } else {
    db_add_answer('GROUP', $group);
  }

  print wrap('Configuring httpd.conf to run Apache as: ' . "\n"
           . 'User: ' . "$user" . ' and Group: ' . "$group" . "\n\n", 0);

  #
  #  Create /var/run/vmware/httpd with the correct user/group
  #

  my $runDir = "/var/run/vmware/httpd";
  my $uid = (getpwnam($user))[2];
  my $gid = (getgrnam($group))[2];
  create_dir($runDir, 0x0);
  safe_chmod(0700, $runDir);
  safe_chown($uid, $gid, $runDir);

  #
  #  Section to update our httpd.conf file
  #
  my $srcConf  = "$instDir/src/apache/conf/httpd.conf";
  my $destConf = "$instDir/apache/conf/httpd.conf";

  my $refPatch;
  $refPatch = updateMuiFiles();
  $$refPatch{"^User.*\$"} = "User $user";
  $$refPatch{"^Group.*\$"} = "Group $group";
  install_file($srcConf, $destConf, $refPatch, 0x1);
}

# Configure remote console: Right now, that means just gtk2 configuration.
sub configure_console {
  # This works, but I think it's not optimal
  configure_gtk2();
}

# switch_to_guest
# Sets links on configuration files we changed during configuration.
# If switch_to_host was never called, do nothing.
sub switch_to_guest {
  my %filesBackedUp;
  my $file;

  if (!defined(db_get_answer_if_exists($cSwitchedToHost))) {
    return;
  }

  %filesBackedUp = db_get_files_to_restore();

  foreach $file (keys %filesBackedUp) {
    if (-l $file) {
      if (check_link($file, $file . db_get_answer($cSwitchedToHost)) eq 'yes') {
        return;
      }
      unlink $file;
      symlink $file . db_get_answer($cSwitchedToHost), $file;
    }
  }
}

# switch_to_host
# Saves configuration files we changed during configuration.
# Sets links on configuration files we backed up during configuration.
sub switch_to_host {
  my $configuredExtension = '.AfterVMwareToolsInstall';
  my %filesBackedUp;
  my $file;

  if (!defined(db_get_answer_if_exists($cSwitchedToHost))) {
    db_add_answer($cSwitchedToHost, $configuredExtension);
  }

  %filesBackedUp = db_get_files_to_restore();

  foreach $file (keys %filesBackedUp) {
    if (-l $file) {
      if (check_link($file, $filesBackedUp{$file}) eq 'yes') {
        return;
      }
      unlink $file;
    } else {
      my %patch;
      undef %patch;
      install_file($file, $file . $configuredExtension, \%patch, 0x1);
      unlink $file;
      # The link might change, do not keep the timestamp.
      db_add_file($file, 0);
    }
    symlink $filesBackedUp{$file}, $file;
  }
}

# Tools configurator
sub configure_tools {
  my $vmwareToolsScript = vmware_product() eq 'tools-for-freebsd' ?
                          '/vmware-tools.sh' : '/vmware-tools';

  if ($gSystem{'invm'} eq 'no') {
    error('This configuration program is to be executed in a '
               . 'virtual machine.' . "\n\n");
  }

  # Check for running over a telnet, ssh or remote X session
  if ((defined $ENV{'REMOTEHOST'} or
       defined $ENV{'SSH_CONNECTION'} or
       defined $ENV{'DISPLAY'} and $ENV{'DISPLAY'} !~ /^:\d/) and
       get_answer('It looks like you are trying to run this program in ' .
                  'a remote session. This program will temporarily shut ' .
                  'down your network connection, so you should only run ' .
                  'it from a local console session. Are you SURE you ' .
                  'want to continue?', 'yesno', 'no') eq 'no') {
    error('Please re-run this program from a local console shell.' . "\n");
  }

  #
  # Stop VMware's services
  #
  print "\n";
  if (!$gOption{'skipstopstart'} &&
      system(shell_string(db_get_answer('INITSCRIPTSDIR') . $vmwareToolsScript)
             . ' stop')) {
    print wrap('Making sure services for ' . vmware_product_name()
                . ' are stopped.' . "\n\n", 0);
    error('Unable to stop services for ' . vmware_product_name() . "\n\n");
  }

  if (vmware_product() eq 'tools-for-linux') {
    # We want to be after networking and syslog
    link_services('vmware-tools', '19', '08');
  } elsif (vmware_product() eq 'tools-for-solaris') {
    link_services_solaris('vmware-tools', '05', '65');
  }

  if (vmware_product() eq 'tools-for-freebsd') {
    configure_module_bsd('vmxnet');
  } elsif (vmware_product() eq 'tools-for-solaris') {
    configure_module_solaris('vmxnet');
  }

  configure_vmmemctl();

  if (vmware_product() eq 'tools-for-linux') {
    configure_vmhgfs();
    write_module_config();
  }

  write_tools_config();

  configure_X();

  # vmware-user and its autostarting only exist on Linux currently
  if (vmware_product() eq 'tools-for-linux') {
    configure_autostart();
  }

  uninstall_file($gConfFlag);

  db_save();
  #
  # Then start VMware's services.
  #
  if (!$gOption{'skipstopstart'} &&
      system(shell_string(db_get_answer('INITSCRIPTSDIR') . $vmwareToolsScript)
             . ' start')) {
    error('Unable to start services for ' . vmware_product_name() . "\n\n");
  } else {
    print "\n";
  }

  print wrap('The configuration of ' . vmware_longname() . ' for this running '
             . 'kernel completed successfully.' . "\n\n", 0);
  # Remind Solaris users currently using the Xsun server to switch to Xorg
  if (vmware_product() eq 'tools-for-solaris' &&
      solaris_10_or_greater() eq 'yes' &&
      direct_command(shell_string($gHelper{'svcprop'}) . ' -p options/server '
                     . 'application/x11/x11-server') =~ /Xsun/) {
    print wrap('You must restart your X session under the Xorg X server before '
               . 'any mouse or graphics changes take effect.  Remember to run '
               . 'kdmconfig(1M) as root to switch from the Xsun server to the '
               . 'Xorg server.' . "\n\n", 0);
  } else {
    print wrap('You must restart your X session before any mouse or graphics changes '
               . 'take effect.' . "\n\n", 0);
  }
  print wrap('You can now run ' . vmware_product_name() . ' by invoking the '
             . 'following command: "' . vmware_tools_app_name() . '" during an '
             . 'X session.' . "\n\n",
             0);

  my $network_path = find_first_exist("/etc/init.d/network",
                                      "/etc/init.d/networking");
  if (vmware_product() eq 'tools-for-linux' and
      db_get_answer('VMXNET_CONFED') eq 'yes') {
    # Because there are problems rmmod'ing the pcnet32 module on a RH7.1
    # 2.4.2-2 kernel the safest way to pick up the vmxnet module is to
    # reboot and not a module exchange.  DO NOT RMMOD pcnet32!  Even by
    # hand! You will terminally confuse the kernel which will panic or
    # hang very unpredictably 
    if ($gSystem{'version_integer'} = kernel_version_integer(2, 4, 2)) {
      print wrap('To make use of the vmxnet driver you will need to '
                 . 'rebooot.' . "\n",0);
    } else {
      print wrap('To use the vmxnet driver, restart networking using the '
	         . 'following commands: ' . "\n"
                 . "$network_path stop" . "\n"
                 . 'rmmod pcnet32' . "\n"
                 . 'rmmod vmxnet' . "\n"
	         . 'depmod -a' . "\n"
	         . 'modprobe vmxnet' . "\n"
                 . "$network_path start" . "\n\n", 0);
    }
  }
  if (vmware_product() eq 'tools-for-freebsd' and
      defined db_get_answer_if_exists('VMXNET_CONFED') and
      db_get_answer('VMXNET_CONFED') eq 'yes') {
    print wrap('Please remember to configure your network by adding:' . "\n"
               . 'ifconfig_vxn0="dhcp"' . "\n"
               . 'to the /etc/rc.conf file and start the network with:'
               . "\n"
               . '/etc/netstart'
               . "\n"
               . 'to use the vmxnet interface using DHCP.' . "\n\n", 0);
  }
  if (vmware_product() eq 'tools-for-solaris' and
      defined db_get_answer_if_exists('VMXNET_CONFED') and
      db_get_answer('VMXNET_CONFED') eq 'yes') {
    print wrap('The installed vmxnet driver will be used for all vlance and '
               . 'vmxnet network devices on this system.  Existing vlance '
               . 'devices will transition from the pcn driver to the vmxnet '
               . 'driver on the next reconfiguration reboot and, as such, their '
               . 'interface names will change from having a "pcn" prefix to a '
               . '"vmxnet" prefix.  You will need to change your network settings '
               . 'accordingly.'
               . "\n\n"
               . 'If you have configured a pcn interface, you should rename its '
               . 'files to use the vmxnet device name to ensure the interface will '
               . 'be brought up properly upon reboot.  For example, the commands '
               . "\n", 0);
    print     (  '  # mv /etc/hostname.pcn0 /etc/hostname.vmxnet0' . "\n"
               . '  # mv /etc/hostname6.pcn0 /etc/hostname6.vmxnet0' . "\n"
               . '  # mv /etc/dhcp.pcn0 /etc/dhcp.vmxnet0'
               . "\n");
    print wrap(  'will cause the Solaris Service Management Facility to bring up '
               . 'the first vmxnet interface using the configuration of your '
               . 'current pcn0 interface.  Note that the hostname6.pcn0 and '
               . 'dhcp.pcn0 files are optional.'
               . "\n\n", 0);
  }
  print wrap('Enjoy,' . "\n\n" . '    --the VMware team' . "\n\n", 0);
}

# switch_tools_config
# Called by the services.sh startup script.
# This allows a switch of configuration depending if the system is
# booted in a VM or natively.
sub switch_tools_config {
  if ($gSystem{'invm'} eq 'yes') {
    switch_to_guest();
  } else {
    switch_to_host();
  }
  db_save();
}

sub get_httpd_status() {
   my $initDir = db_get_answer('INITSCRIPTSDIR');
   my $script = "$initDir/httpd.vmware";
   my $command = "$script status";
   local *FD;

   if (file_name_exist($script)) {
      if (!open(FD, "$command |")) {
         return 3;
      }
      while(<FD>) {
         if ( /\s*.*stopped.*/ ) {
            return 3;
         } else {
            return 0;
         }
      }
   }
   return 3;
}

sub configure_gtk2() {
  my $confs = db_get_answer('LIBDIR') . '/libconf';
  my $pangorc = $confs . '/etc/pango/pangorc';
  my $pangoModules = $confs . '/etc/pango/pango.modules';
  my $pangoxAliases = $confs . '/etc/pango/pangox.aliases';
  my $gdkPixbufLoaders = $confs . '/etc/gtk-2.0/gdk-pixbuf.loaders';
  my $gtkIMModules = $confs . '/etc/gtk-2.0/gtk.immodules';
  local *RC;
  local *FD;
  local *TFD;
  my $base;

  print wrap('Configuring fallback GTK+ 2.4 libraries.' . "\n\n", 0);

  if (!open(RC, "$pangorc")) {
    error("Unable to open $pangorc\n");
    return;
  }
  while(<RC>) {
    if (/ModuleFiles = (.*)\/etc\/pango\/pango.modules/) {
      $base = $1;
      last;
    }
  }
  close RC;

  if ($base eq "") {
    error("Unable to parse base from $pangorc\n");
    return;
  }

  my @files = ($pangorc, $pangoModules, $pangoxAliases, $gdkPixbufLoaders,
               $gtkIMModules);

  foreach my $file (@files) {
    my $tmp = "$file.tmp";

    if (!open(FD, "$file")) {
      error("Unable to open $file");
    }

    if (!open(TFD, ">$tmp")) {
      error("Unable to open $tmp");
    }

    while(<FD>) {
      my $line = $_;
      $line =~ s|$base|$confs|e;
      printf TFD $line;
    }
    close FD;
    close TFD;

    my $ret = `mv $tmp $file`;
    # XXX do something with ret

    # "update" timestamp in the install db
    db_remove_file($file);
    db_add_file($file, 0x1);
  }
}

# Returns the console name of the product for use in a .desktop file
sub getDesktopConsoleName {
   if (vmware_product() eq "wgs" || vmware_product() eq "vserver") {
      return vmware_product_name() . " Console";
   } else {
      return vmware_product_name();
   }
}

# Returns the name of the .desktop file to produce
sub getDesktopFileName {
   if (vmware_product() eq "ws") {
      return "vmware-workstation.desktop";
   } elsif (vmware_product() eq "wgs") {
      return "vmware-server.desktop";
   } elsif (vmware_product() eq "vserver") {
      return "vmware-server.desktop";
   }

   return undef;
}

# Returns the name of the icon file to produce
sub getIconFileName {
   if (vmware_product() eq "ws") {
      return "vmware-workstation.png";
   } elsif (vmware_product() eq "wgs") {
      return "vmware-server.png";
   } elsif (vmware_product() eq "vserver") {
      return "vmware-server.png";
   }

   return undef;
}

# Return whether or not this is a hosted desktop product.
sub isDesktopProduct {
   return vmware_product() eq "ws" || vmware_product() eq "player";
}

# Return whether or not this is a hosted server product.
sub isServerProduct {
   return vmware_product() eq "wgs" ||
          vmware_product() eq "vserver" ||
          vmware_product() eq "console";
}

# Creates a .desktop file
sub createDesktopFile {
   my $use_desktop_utils = shift;
   my $mime_support = shift;
   my $desktopFilename = shift;
   my $productName = shift;
   my $iconName = shift;
   my $execName = shift;
   my $comment = shift;
   my $mimetypes = shift;
   my $visible = shift;
   my $desktopConf;
   my $tmpdir;

   $tmpdir = make_tmp_dir($cTmpDirPrefix);
   $desktopConf = "$tmpdir/$desktopFilename";

   if (!open(DESKTOP, ">$desktopConf")) {
        print STDERR wrap("Couldn't open \"$desktopConf\".\n"
                          . "Unable to create the .desktop menu entry file. "
                          . "You must add it to your menus by hand.\n", 0);
      remove_tmp_dir($tmpdir);
      return;
   }

   print DESKTOP <<EOF;
[Desktop Entry]
Encoding=UTF-8
Name=$productName
Comment=$comment
Exec=$execName
Terminal=false
Type=Application
Icon=$iconName
StartupNotify=true
Categories=Application;System;
X-Desktop-File-Install-Version=0.9
MimeType=$mimetypes
EOF

   if ($visible == 0) {
      print DESKTOP "NoDisplay=true\n";
   }

   close(DESKTOP);

   safe_chmod(0644, $desktopConf);

   install_symlink(db_get_answer("ICONDIR") . "/hicolor/48x48/apps/$iconName",
                   db_get_answer("PIXMAPDIR") . "/$iconName");

   my $desktopdir = db_get_answer("DESKTOPDIR");

   if ($use_desktop_utils == 1) {
      my $params = "";

      if ($mime_support == 1) {
         $params = "--rebuild-mime-info-cache ";
      }

      if (system("desktop-file-install --vendor=vmware " .
                 "--dir=" . shell_string($desktopdir) . " " .
                 $params . shell_string($desktopConf))) {
         print STDERR wrap("Unable to install the .desktop menu entry file. "
                           . "You must add it to your menus by hand.\n", 0);
         remove_tmp_dir($tmpdir);
         return;
      }
      db_add_file("$desktopdir/$desktopFilename", 1);
   } else {
      my %p;
      undef %p;
      install_file($desktopConf, "$desktopdir/$desktopFilename", \%p, 1);
   }

   remove_tmp_dir($tmpdir);
}

# Determine the directory for the icon and .desktop file, and install them
sub configureDesktopFiles {
   my $use_desktop_utils = 1;
   my $mime_support = 0;
   my $pixmapdir;
   my $desktopdir;

   if (!isServerProduct() && !isDesktopProduct()) {
      return;
   }

   # NOTE: We don't uninstall the desktop file if we used
   #       desktop-file-install, because there is no desktop-file-uninstall.
   $desktopdir = db_get_answer_if_exists("DESKTOPDIR");
   if (defined($desktopdir)) {
      # Uninstall
      uninstall_prefix($desktopdir);
   }

   $pixmapdir = db_get_answer_if_exists("PIXMAPDIR");
   if (defined($pixmapdir)) {
      # Uninstall
      uninstall_prefix($pixmapdir);
   }

  $desktopdir = get_persistent_answer(
     "What directory contains your desktop menu entry files? "
     . "These files have a .desktop file extension.",
     "DESKTOPDIR", "dirpath",
     "/usr/share/applications");

   if (internal_which("desktop-file-install") eq "") {
      $use_desktop_utils = 0;
      create_dir($desktopdir, 0x1);
   } else {
      my $buf = `desktop-file-install --help 2>&1`;

      if ($buf =~ /--rebuild-mime-info-cache/) {
         $mime_support = 1;
      }
   }

   $pixmapdir = get_persistent_answer("In which directory do you want to "
                                      . "install the application's icon?",
                                      "PIXMAPDIR", "dirpath",
                                      "/usr/share/pixmaps");
   create_dir($pixmapdir, 0x1);

   if (vmware_binary() ne "vmplayer") {
      my $mimetypes = "application/x-vmware-vm;";

      if (vmware_product() eq "ws") {
         $mimetypes .= "application/x-vmware-team;";
      }

      createDesktopFile($use_desktop_utils, $mime_support,
                        getDesktopFileName(), getDesktopConsoleName(),
                        getIconFileName(), vmware_binary(),
                        "Run and manage virtual machines",
                        $mimetypes, 1);

      if (isServerProduct()) {
         createDesktopFile($use_desktop_utils, $mime_support,
                           "vmware-console-uri-handler.desktop",
                           getDesktopConsoleName(), getIconFileName(),
                           vmware_binary() . " -o %f",
                           "Run and manage remote virtual machines",
                           "application/x-vmware-console;", 0);
      }
   }

   if (isDesktopProduct()) {
      # Player is bundled with all desktop products.
      createDesktopFile($use_desktop_utils, $mime_support,
                        "vmware-player.desktop", "VMware Player",
                        "vmware-player.png",
                        "vmplayer", "Run a virtual machine",
                        "application/x-vmware-vm;", 1);
   }
}

# Creates a mimetype package description file
sub createMimePackageFile {
   my $tmpdir;
   my $mimeConf;
   my $mimePath;
   my $mimePackagePath;
   my $desticondir;
   my %p;

   if (!isServerProduct() && !isDesktopProduct()) {
      return;
   }

   $mimePath = "/usr/share/mime";
   $mimePackagePath = $mimePath . "/packages";

   # Uninstall
   uninstall_prefix($mimePackagePath);

   # Create the new mimetype package
   create_dir($mimePackagePath, 0x1);
   $tmpdir = make_tmp_dir($cTmpDirPrefix);
   $mimeConf = "$tmpdir/vmware.xml";

   if (!open(MIMEPACKAGE, ">$mimeConf")) {
      print STDERR wrap("Couldn't open \"$mimeConf\".\n"
                    . "Unable to create the MIME-Type package file.\n", 0);
      remove_tmp_dir($tmpdir);
      return;
   }

   print MIMEPACKAGE <<EOF;
<?xml version="1.0" encoding="UTF-8"?>

<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
 <mime-type type="application/x-vmware-vm">
  <comment xml:lang="en">VMware virtual machine</comment>
  <magic priority="50">
   <match type="string" value='config.version = "' offset="0:4096"/>
  </magic>
  <glob pattern="*.vmx"/>
 </mime-type>

 <mime-type type="application/x-vmware-vmdisk">
  <comment xml:lang="en">VMware virtual disk</comment>
  <magic priority="50">
   <match type="string" value="# Disk DescriptorFile" offset="0"/>
   <match type="string" value="KDMV" offset="0"/>
  </magic>
  <glob pattern="*.vmdk"/>
 </mime-type>

 <mime-type type="application/x-vmware-team">
  <comment xml:lang="en">VMware team</comment>
  <magic priority="50">
   <match type="string" value='&lt;Foundry version="1"&gt;' offset="0">
    <match type="string" value="&lt;VMTeam&gt;" offset="23:24"/>
   </match>
  </magic>
  <glob pattern="*.vmtm"/>
 </mime-type>

 <mime-type type="application/x-vmware-snapshot">
  <comment xml:lang="en">VMware virtual machine snapshot</comment>
  <magic priority="50">
   <match type="string" value="\\0xD0\\0xBE\\0xD0\\0xBE" offset="0"/>
  </magic>
  <glob pattern="*.vmsn"/>
 </mime-type>

 <mime-type type="application/x-vmware-vmfoundry">
  <comment xml:lang="en">VMware virtual machine foundry</comment>
  <magic priority="50">
   <match type="string" value='&lt;Foundry version="1"&gt;' offset="0">
    <match type="string" value="&lt;VM&gt;" offset="23:24"/>
   </match>
  </magic>
  <glob pattern="*.vmxf"/>
 </mime-type>

EOF

   if (isServerProduct()) {
      print MIMEPACKAGE <<EOF
 <mime-type type="application/x-vmware-console">
  <comment xml:lang="en">VMware remote virtual machine</comment>
  <magic priority="20">
   <match type="string" value="-h " offset="0">
    <match type="string" value="-P " offset="3:4096"/>
    <match type="string" value="-u " offset="3:4096"/>
    <match type="string" value="vmx" offset="3:4096"/>
   </match>
  </magic>
  <glob pattern="*.xvm"/>
 </mime-type>

EOF
   }

   print MIMEPACKAGE "</mime-info>\n";

   close MIMEPACKAGE;

   safe_chmod(0644, $mimeConf);

   undef %p;
   install_file($mimeConf, $mimePackagePath . "/vmware.xml", \%p, 1);

   remove_tmp_dir($tmpdir);

   # Update the MIME database
   if (internal_which("update-mime-database") ne "") {
      if (system("update-mime-database " . shell_string($mimePath) .
                 " >/dev/null 2>&1")) {
         print STDERR wrap("Unable to update the MIME-Type database.\n", 0);
         return;
      }
   }

   $desticondir = get_persistent_answer(
      "In which directory do you want to install the mime type icons?",
      "ICONDIR", "dirpath", "/usr/share/icons");

   undef %p;
   install_dir(db_get_answer('LIBDIR') . '/share/icons',
               $desticondir . "/hicolor", \%p);
   # Refresh icon cache. Some systems (Ubuntu) don't do it automatically
   system(internal_which('touch') . ' -m ' . shell_string('/usr/share/icons/hicolor/'));
   system(shell_string(internal_which('gtk-update-icon-cache')) . ' >/dev/null 2>&1');
}

# Program entry point
sub main {
   my (@setOption, $opt);

   if (not is_root()) {
      error('Please re-run this program as the super user.' . "\n\n");
   }

   # Force the path to reduce the risk of using "modified" external helpers
   # If the user has a special system setup, he will will prompted for the
   # proper location anyway
   $ENV{'PATH'} = '/bin:/usr/bin:/sbin:/usr/sbin';

   initialize_globals();
   if (not (-e $gInstallerMainDB)) {
      error('Unable to find the database file (' . $gInstallerMainDB . ')'
            . "\n\n");
   }
   db_load();
   db_append();
   initialize_external_helpers();

   $gOption{'default'} = 0;
   $gOption{'compile'} = 0;
   $gOption{'prebuilt'} = 0;
   $gOption{'skipstopstart'} = vmware_product() eq 'server';

   if (vmware_product() eq 'tools-for-freebsd') {
      setupTclOrGtkSymlinks();
   }
   if (vmware_product() eq 'tools-for-linux' ||
       vmware_product() eq 'tools-for-freebsd' ||
       vmware_product() eq 'tools-for-solaris') {
       setup32or64Symlinks();
   }
   # Have other gOption values set by system_info()
   if (vmware_product() ne 'mui' &&  vmware_product() ne 'console') {
      system_info();
   }

   # List of questions answered with command-line arguments
   @setOption = ();
   # Command line analysis
   while ($#ARGV != -1) {
      my $arg;

      $arg = shift(@ARGV);
      if (lc($arg) =~ /^(-)?(-)?d(efault)?$/) {
         $gOption{'default'} = 1;
      } elsif (lc($arg) =~ /^(-)?(-)?c(ompile)?$/) {
         $gOption{'compile'} = 1;
      } elsif (lc($arg) =~ /^(-)?(-)?p(rebuilt)?$/) {
         $gOption{'prebuilt'} = 1;
      } elsif (lc($arg) =~ /^(-)?(-)?t(ry-modules)?$/) {
         $gOption{'try-modules'} = 1;
      } elsif (lc($arg) =~ /^(-)?(-)?s(witch)?$/) {
         $gOption{'tools-switch'} = 1;
      } elsif (lc($arg) =~ /^(-)?(-)?overwritesvga?$/) {
	 # This option is deprecated, we always overwrite the svga driver.
         $gOption{'overwriteSVGA'} = 1;
      } elsif (lc($arg) =~ /^-skipstopstart/) {
         $gOption{'skipstopstart'} = 1;
      } elsif ($arg =~ /=yes/ || $arg =~ /=no/) {
         push(@setOption, $arg);
      } else {
         config_usage();
      }
   }

   if (vmware_product() eq 'mui') {
      $gSystem{'distribution'} = distribution_info();
      configure_mui();
      uninstall_file($gConfFlag);
      db_save();
      print wrap('The configuration of ' . vmware_product_name()
                 . ' completed successfully.' . "\n\n", 0);
      exit 0;
   }

   if (vmware_product() eq 'console') {
      show_EULA();
      configure_console();
      uninstall_file($gConfFlag);
      db_save();
      print wrap('The configuration of ' . vmware_product_name()
         . ' completed successfully.' . "\n\n", 0);
      exit 0;
   }

   if (($gOption{'compile'} == 1) && ($gOption{'prebuilt'} == 1)) {
      print wrap('The "--compile" and "--prebuilt" command line options are '
                 . 'mutually exclusive.' . "\n\n", 0);
      config_usage();
   }

   $gFirstModuleBuild = 1;

   # Tools configurator entry point
   if (vmware_product() eq 'tools-for-linux' ||
       vmware_product() eq 'tools-for-freebsd' ||
       vmware_product() eq 'tools-for-solaris') {
      if ($gOption{'tools-switch'} == 1) {
         switch_tools_config();
      } else {
         configure_tools();
      }
      exit 0;
   }

   # Build the list of all and available ethernet adapters
   # The first list is all the adapters that we have.  The
   # second are ones that we can still be bridged.
   load_all_ethif_info();
   load_ethif_info();

   # Stop VMware's services
   if (!$gOption{'skipstopstart'}) {
      print wrap('Making sure services for ' . vmware_product_name()
                 . ' are stopped.' . "\n\n", 0);
      if (system(shell_string(db_get_answer('INITSCRIPTSDIR') . '/vmware') .
                  ' status vmcount') >> 8 == 2 &&
          get_answer('Do you want to force a shutdown on the running VMs?',
                     'yesno', 'no') eq 'no') {
         error('Please shut down any running VMs and run this script again.' .
               "\n\n");
      } else {
         if (system(shell_string(db_get_answer('INITSCRIPTSDIR') . '/vmware')
                    . ' stop')) {
            error('Unable to stop services for ' . vmware_product_name() .
                  "\n\n");
         }
     }
   }
   print "\n";

   if (@setOption > 0) {
      $gOption{'default'} = 1;
      # User must specify 'EULA_AGREED=yes' on the command line
      db_add_answer('EULA_AGREED', 'no');
   }
   # Install answers specified on the command line
   foreach $opt (@setOption) {
      my ($key, $val);
      ($key, $val) = ($opt =~ /^([^=]*)=([^=]*)/);
      print $key, ' = ', $val, "\n";
      db_add_answer($key, $val);
   }

  show_EULA();

  if (vmware_product() eq 'wgs' ||
      vmware_product() eq 'vserver') {
    # Check memory requirements for GSX/WGS/VMware Server
    check_wgs_memory();
  }
  if (vmware_product() ne 'server') {
    configure_gtk2();
    createMimePackageFile();
    configureDesktopFiles();
    configure_mon();
    configure_pp();
    configure_net();
    build_vmnet();
  }

  # Create the directory for the UNIX domain sockets
  create_dir($cConnectSocketDir, 0x1);
  safe_chmod(0755, $cConnectSocketDir);
  # Cleanup the directory. It is important to start from a fresh state, for
  # example when the permission scheme changes (which happened between WS 4.0.1
  # and WS 4.0.2). --hpreg
  {
    my $dir;
    # 3 means the httpd process is not running. This is equivalent to saying
    # '/etc/init.d/httpd.vmware status'
    my $httpdStatus = get_httpd_status();
    my $initDir = db_get_answer('INITSCRIPTSDIR');

      if ($httpdStatus != 3) {
         # stopping the httpd process to get a fresh name pipe on /var/run/vmware/httpd
         system("$initDir/httpd.vmware stop");
      }
      foreach $dir (internal_ls($cConnectSocketDir)) {
         remove_tmp_dir($cConnectSocketDir . '/' . $dir);
      }
      if ($httpdStatus != 3) {
         # starting httpd if previously stopped
         system("$initDir/httpd.vmware start");
      }
   }

   if (vmware_product() ne 'wgs' &&
       vmware_product() ne 'vserver' &&
       vmware_product() ne 'server' &&
       defined($gDBAnswer{'NETWORKING'}) && get_samba_net() != -1) {
      unconfigure_samba();
   }
   if (vmware_product() eq 'wgs' ||
       vmware_product() eq 'vserver' ||
       vmware_product() eq 'server') {
      configure_wgs();
      configure_security();
   }
   if (vmware_product() eq 'wgs' ||
       vmware_product() eq 'vserver') {
      configure_serverd();
   }

  if (vmware_product() ne 'server') {
     # We want VMware to start before samba. If this becomes messy in the future
     # we will probably have to dynamically determine the right priority to use
     # based on dependencies on other services as we do in the tools install.
     my $S_priority;
     if ($gSystem{'distribution'} eq 'suse') {
        # samba is 20 SuSE
        $S_priority = '19';
     } else {
        # samba is 91 on RedHat
        $S_priority = '90';
     }
     link_services("vmware", $S_priority, "08");
  }
  write_vmware_config();
  if (vmware_product() eq 'wgs' ||
      vmware_product() eq 'vserver') {
    # This must come after write_vmware_config()
    check_license();
  }
  # Remove the flag _before_
  uninstall_file($gConfFlag);
  db_save();
  # Then start VMware's services
  if (!$gOption{'skipstopstart'}) {
    system(shell_string(db_get_answer('INITSCRIPTSDIR') . '/vmware') . ' start');
    print "\n";
  }

  show_PROMOCODE();

  print wrap('The configuration of ' . vmware_longname() . ' for this ' .
             'running kernel completed successfully.' . "\n\n", 0);
  if (vmware_product() ne 'wgs' &&
      vmware_product() ne 'vserver' &&
      vmware_product() ne 'server') {
    print wrap('You can now run ' . vmware_product_name() . ' by invoking' .
               ' the following command: "' . db_get_answer('BINDIR') .
               '/vmware".' . "\n\n", 0);
    print wrap('Enjoy,' . "\n\n" . '    --the VMware team' . "\n\n", 0);
  }

  if (vmware_product() eq 'wgs' ||
      vmware_product() eq 'vserver' ||
      vmware_product() eq 'server') {
    my $muiConfig = internal_which('vmware-config-mui.pl');
    if ($muiConfig ne '') {
      if (get_answer('Setup found that the VMware Management Interface is installed on your machine. ' .
                     'The VMware Management Interface configurator (' . $muiConfig . ') needs to be run. ' .
                     'Do you want to run this program now?', 'yesno', 'yes') eq 'yes') {
        system($muiConfig);
      }
    }
  }
  exit(0);
}


main();

```

---

### Post by fjgaude on 2008-03-10
In what directory did you extract the vmware? What else was done? Where are the rest of the vmware files? They should be in /usr/bin.

It should be in /usr/bin folders. Mine is. I have no idea how it got into /usr and not in /usr/bin.

---

### Post by niko123 on 2008-03-10
well when i installed vmware i installed everything in defult...and now that i remember it did go from /usr/ to /usr/bin and now that im looking... 

all the files are in /usr and /usr/bin

are all the files supposed to only be in /usr?

---

### Post by fjgaude on 2008-03-10
In the cases I've seen they are all in /usr/bin as they a scripts, executables. There no files in /usr, just folders.

---

### Post by niko123 on 2008-03-10
well this is what i seem to have....this is what is in
/usr
[IMG]http://i22.photobucket.com/albums/b303/xtwoface/Screenshot-1.png[/IMG]

and this is what i have in /usr/bin
[IMG]http://i22.photobucket.com/albums/b303/xtwoface/Screenshot-1-1.png[/IMG]

---

### Post by niko123 on 2008-03-11
bump

---

### Post by fjgaude on 2008-03-11
I don't know what to tell you... when the install occurred somehow the two different directories must have been indicated.

Are you able to get anything working correctly?

---

### Post by alphaniner on 2008-03-14
try

```
cd /usr
```

```
./vmware-config.pl
```
or
```
sudo ./vmware-config.pl
```
if necessary

---

