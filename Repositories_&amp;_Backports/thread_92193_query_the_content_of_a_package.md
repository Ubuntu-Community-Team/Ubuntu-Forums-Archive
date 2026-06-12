---
title: "query the content of a package"
date: 2005-11-18
forum: Repositories &amp; Backports
---

### Post by hil on 2005-11-18
I am running Kubuntu 5.10 Breezy on IBM thinkpad T30. Everythings works fine except the fact that I don't know how to query the content of a package in the repository or from a file (.deb). I was a Fedora user. In Fedora or any RPM based distribution, users can do rpm -qlpi FILENAME.rpm to query the files that will be installed on the system. Can I do this in ubuntu? Please help me.

---

### Post by yoyoned on 2005-11-19
```

 pkg-query --help
```gives the following output```

Usage: dpkg-query [<option>] <command>
Commands:
  -s|--status <package-name> ...      display package status details
  -p|--print-avail <package-name> ... display available version details
  -L|--listfiles <package-name> ...   list files `owned' by package(s)
  -l|--list [<pattern> ...]           list packages concisely
  -W|--show <pattern> ...             show information on package(s)
  -S|--search <pattern> ...           find package(s) owning file(s)
  --help | --version                  show this help / version number
  --licence                           print copyright licensing terms

Options:
  --admindir=<directory>     Use <directory> instead of /var/lib/dpkg
  -f|--showformat=<format>   Use alternative format for --show

Format syntax:
  A format is a string that will be output for each package. The format
  can include the standard escape sequences \n (newline), \r (carriage
  return) or \\ (plain backslash). Package information can be included
  by inserting variable references to package fields using the ${var[;width]}
  syntax. Fields will be right-aligned unless the width is negative in which
   case left aligenment will be used.


```

For example ```
dpkg-query -L lynx

```
would give you a list of files installed by lth package lynx.

---

### Post by Lambert on 2005-11-19
apt-cache is the command for packages in the repository.



apt-cache [options] command

Commands:
   add - Add a package file to the source cache
   gencaches - Build both the package and source cache
   showpkg - Show some general information for a single package
   showsrc - Show source records
   stats - Show some basic statistics
   dump - Show the entire file in a terse form
   dumpavail - Print an available file to stdout
   unmet - Show unmet dependencies
   search - Search the package list for a regex pattern
   show - Show a readable record for the package
   depends - Show raw dependency information for a package
   rdepends - Show reverse dependency information for a package
   pkgnames - List the names of all packages
   dotty - Generate package graphs for GraphVis
   xvcg - Generate package graphs for xvcg
   policy - Show policy settings

Options:
  -h   This help text.
  -p=? The package cache.
  -s=? The source cache.
  -q   Disable progress indicator.
  -i   Show only important deps for the unmet command.
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-cache(8) and apt.conf(5) manual pages for more information.

---

