---
title: "how to get a tree from the ftp"
date: 2011-03-22
forum: Server Platforms
---

### Post by coibyxqx on 2011-03-22
Hi, I'm wondering if there exists a program get can build a tree from the ftp?
Thanks!

---

### Post by Daedalus_357 on 2011-03-22
Filezilla + Screenshots?

other than that, i don't know of any, but maybe someone else does!

---

### Post by coibyxqx on 2011-03-23
> **Daedalus_357 said:**
> Filezilla + Screenshots?

other than that, i don't know of any, but maybe someone else does!

Screenshots cannot copy words, thanks any way!

---

### Post by egpetrich on 2011-03-26
I may be able to help you. I wrote a small Perl script to do what I think you requested, but it has some strong dependencies on the FTP server.

The biggest problem is that FTP was "meant" for humans to read. There's no guarantee of consistent format in the directory listings that it returns. Programs like FileZilla have special code dedicated to understanding the more common formats, but there's always a chance that the FTP server is configured with an uncommon format.

My script depends on three things:
[LIST]
[*]The FTP server must understand the option "-R" (recursive).
[*]The file list created by "ls -R" must show each directory name separately.
[*]You need to have the Perl module Net::FTP installed, but it probably is already.
[/LIST]

So, if you're willing to trust me, create a file containing the following code:

```
#!/usr/bin/perl -w
# Test script to return a complete tree of the directories available over
# an FTP connection.
#

use Net::FTP;

if (int(@ARGV) < 1) {
    print "$0 hostname [dirname]\n";
    exit(1);
}
my $hostname = shift(@ARGV);
my %dir_tree = ();
my $ftp = Net::FTP->new($hostname, Debug => 0)
  or die "Cannot connect to '$hostname': $@";

$ftp->login()
  or die "Cannot login ", $ftp->message;
if (int(@ARGV) > 0) {
    $ftp->cwd($ARGV[0])
	or die("Could not get dir ", $ftp->message);
}
my $cwd = $ftp->pwd();
my @dir_list = $ftp->dir("-R");
foreach my $line (@dir_list) {
    if ($line =~ m/^(\S+):/) {
	my $tree_ref = \%dir_tree;
	foreach my $dir (split(/\//, $1)) {
	    if (! exists($tree_ref->{$dir})) {
		$tree_ref->{$dir} = {};
	    }
	    $tree_ref = $tree_ref->{$dir};
	}
    }
}
$ftp->quit;

print("$cwd\n");
&show_dir_tree(\%dir_tree, "");

exit(0);

sub show_dir_tree {
    my ($tree_ref, $indent_str) = @_;
    my $num_entries = int(keys(%$tree_ref));
    my $entry_num = 1;
    foreach my $x (sort(keys(%$tree_ref))) {
	print $indent_str . (($entry_num < $num_entries) ? "|-" : "\\-") . $x . "\n";
	&show_dir_tree($tree_ref->{$x}, $indent_str . (($entry_num < $num_entries) ? "| " : "  "));
	++$entry_num;
    }
    return;
}

```

Save the file (I call it "ftp_dir_tree.pl") and make it executable with:
```
chmod ug+x ./ftp_dir_tree.pl
```
This utility assumes that your FTP connection information is stored in the file "~/.netrc". (This avoids keeping passwords in publicly-accessible files.) The format of "~/.netrc" is pretty simple, with each line like this:
```
machine ftp.example.com login my_username password my_password
```
You can then view a tree with this command:
```
./ftp_dir_tree.pl ftp.example.com
```
If it works for you the way it does for me, you should see something like this:
```
/home/my_username
|-.ssh
|-photos
| |-vacation
| |-work
| \-funny_people
|-bin
|-lib
| \-perl5
|   \-site_perl
|     \-5.6.1
|       |-Net
|       \-i386-linux
|         \-auto
|           \-Net
|             \-Wake
...etc...
```
You can also specify a directory name (either relative or absolute) on the command line, as in:
```
./ftp_dir_tree.pl ftp.example.com photos
```
I hope this proves useful.

---

