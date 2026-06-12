---
title: "perl DBI behaves strange with apache"
date: 2007-06-24
forum: Server Platforms
---

### Post by TomFumb on 2007-06-24
Hi and thanks for looking,
I have a very simple perl script which sits in /var/www/cgi-bin and uses the DBI module. It looks like this...

#!/usr/bin/perl

use DBI;

print "Content-Type: text/html\n\n";
print "<html><head></head><body><p>Here is some text</p>";

# Establish database connection
my $dbh = DBI->connect( 'dbi:Oracle:XE',
        'user',
        'pass',
        {AutoCommit => 1}
        ) || die "Database connection not made: $DBI::errstr";

        $sql = qq{ select count(id) from tom.temp_loc };
        $sth = $dbh->prepare( $sql );
        $sth->execute();
        $sth->bind_columns( undef, \$userCount );
        while($sth->fetch () )
                {
                print "<p>".$userCount."</p>";
                }

print "</body></html>";


I can run this script from the command line, and it runs through as expected, so I know that I am making my database connection, and retreiving data without a problem. When I run it through apache, at [http://localhost/cgi-bin/test.pl](http://localhost/cgi-bin/test.pl), it executes, but only prints the first line of text, and none of the database output, or the closing html. 

Does anyone know why this might be happening? I could understand if the script wasn't working full stop, or if the db connection was failing, but as far as I can see there's nothing wrong here

Any help with this would be very much appreciated, I need to run a local server for a project I'm working on at uni.

tom


p.s. (Edit) Could this be something to do with a timeout on apache - where it gives up waiting to connect to the database?
by the way I'm using Apache2, the latest perl modules, and Oracle 10g2 eXpress Edition

---

### Post by tr333 on 2007-06-27
Instead of writing CGI output directly, use the [CGI](http://search.cpan.org/~lds/CGI.pm-3.29/CGI.pm) module available from CPAN.  If you are using perl for CGI, you should probably use the "-T" switch to turn on 'taint' mode.  This will add extra security checks to secure your CGI script against malicious use.

To get more information on any possible errors, check the apache log files located in /var/log/apache2/, specifically access.log and error.log.

---

### Post by TomFumb on 2007-06-28
tr333, many thanks for your advice, I'll certainly be making my scripts more secure, as I'm thinking about making my server a little more public

I managed to solve my problem, and as I kind of expected, it was my own dumb fault - I left out this crucial line - 

$ENV{'ORACLE_HOME'} = '/usr/lib/oracle/xe/app/oracle/product/10.2.0/server';

This makes sense as in the terminal this variable is set in ~/.bashrc, so as a user I wasn't having any trouble, but as apache user, oracle_home was undefined.

thanks again for your help, sorry the problem wasn't a little juicier

tom

---

