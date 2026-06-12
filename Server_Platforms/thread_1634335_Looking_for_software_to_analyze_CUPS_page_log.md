---
title: "Looking for software to analyze CUPS page_log"
date: 2010-11-30
forum: Server Platforms
---

### Post by MrNatewood on 2010-11-30
Hello,

Does anybody know an application that sums up the printing from the page_log file and puts the summed amounts in another simple text file?
Tried phpPrintAnalyzer but could not figure out how to set it up.

Running Ubuntu Hardy LTS server.

Any other ideas or instructions on phpPrintAnalyzer?

Thanks.

---

### Post by tgalati4 on 2010-11-30
What specifically did you have trouble with when you tried to install phpPrintAnalyzer?

You need a working, current LAMP stack installed on Hardy Server.  You need to install jpgraph extensions for PHP to get the plots. [http://jpgraph.net/](http://jpgraph.net/)

Looking through the INSTALL.txt file, there is a dummy configuration file that you need to copy over and make changes to.  You have to place the files somewhere in your /var/www path.  Since you are running Hardy Server, I presume you have apache2 running and hosting a website or two.  If so, then put the files somewhere in the path of an existing website tree.  Point your browser (from a remote machine) to the [http://hostname_address/myprintjobs/index.php](http://hostname_address/myprintjobs/index.php) and it should filter and display your print jobs.  This assumes that index.php and the rest of the analyzer files are in /var/www/myprintjobs.

Some issues that may come up:

I believe Hardy's LAMP stack uses PHP5 by default.  This phpPrintAnalyzer was written in PHP4 (March 2004 vintage code!!), so you need to install php4 along side PHP5.  Normally this is OK, but breakage could occur, so proceed carefully:

sudo apt-get install php4

You might look at the php4 code and modify it to be php5 compatible.  I don't know if there are automated tools to do this.  The alternative is to try running it with PHP5 without installing PHP4 and see how much functionality the print analyzer has.  Then modify the broken bits of PHP4 code to be PHP5 compatible.

All of this seems like a lot of work for print summaries.  You probably need to search for a Perl script to just gives you the summaries.  Something like [http://www.nongnu.org/printanalyze/](http://www.nongnu.org/printanalyze/) and another: [http://www.feferraz.net/en/P/Cartridge_usage_monitoring_in_CUPS](http://www.feferraz.net/en/P/Cartridge_usage_monitoring_in_CUPS)

And from the SAMBA documentation:

Other Accounting Tools

Other accounting tools that can be used includes: PrintAnalyzer, pyKota, printbill, LogReport. For more information regarding these tools you can try a Google search.

---

### Post by MrNatewood on 2010-12-02
Thanks.
Tried Lire and it works great.

---

