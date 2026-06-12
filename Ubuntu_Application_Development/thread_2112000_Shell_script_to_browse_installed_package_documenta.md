---
title: "Shell script to browse installed package documentation"
date: 2013-02-03
forum: Ubuntu Application Development
---

### Post by schragge on 2013-02-03
Attached tarball ([ATTACH]242174[/ATTACH]) contains shell scripts to browse documentation installed in /usr/share/doc

They are similar in function to [debmany(1)]("http://manpages.ubuntu.com/cgi-bin/search.py?q=debmany") from the package debian-goodies.

The main script is doc.bash. Just rename it 'doc' and put somewhere on $PATH. For convenience, I also prepared a very basic .deb with it. It's [here]("https://www.box.com/s/e0y3s4w4431z8u7e9e1w") (unsigned). The source package is there, too.

**Contents of the tarball**
[LIST]
[*] doc.bash - this is all you need. 
[*] doc.sh - the same script rewritten for /bin/sh. 
[*] doc.posix.sh - ditto, strictly POSIX-compliant. 
[*] doc.legacy.sh - ditto, for legacy Bourne shell. 
[*] doc.select.* - dumbed down versions using 'select' (bash and zsh). 
[*] completion.* - completion code (bash and tcsh). 
[*] compctl.zsh - completion code for zsh, using the 'old' completion subsystem. 
[*] compsys.zsh - ditto, using the 'new' completion subsystem. 
[*] _doc - completion function for zsh (to put in $fpath). 
[*] doc - completion function for yash (to put in $YASH_LOADPATH). 
[/LIST]

For most purposes, the simplified versions (doc.select.*) should be enough. Below is the code of 'doc.select.bash'. It gives the idea of what the scripts do.
```

#!/bin/bash -e
[[ -n $1 ]] || { echo "Usage: $0 package_name" >&2; exit 1;}
docpfx=/usr/share/doc/
[[ -d $docpfx$1 ]] || { echo "Directory $docpfx$1 not found" >&2; exit 2;}
: ${COLUMNS:=`tput cols`}
GLOBIGNORE=AUTHORS*:ACK*:CONTRIBUTORS*:CREDITS*:THANKS*
lsopts='-Ldpq --group-directories-first'
shopt -s extglob nullglob checkwinsize
idx=index?(.[a-z][a-z]*).htm?(l) CDPATH=

docmenu () {
  pushd "$1" >/dev/null
  local PS3="...${PWD#$docpfx}> "
  # Grouping index.html first, directories next, then all the rest.
  local -a files=($idx)
  mapfile -tO${#files[@]} files < <(ls $lsopts !($idx))
  select file in "${files[@]}"; do
    [[ $REPLY == [Xx]* ]] && exit
    [[ -z $file ]] && break
    if [[ -d $file ]]; then
      docmenu "$file"
    else
      case $file in
        *.htm?(l)) sensible-browser "$file";;
        *)         sensible-pager   "$file";;
      esac
    fi
  done
  popd >/dev/null
}

pushd "$docpfx" >/dev/null
docmenu "$1"
popd >/dev/null

```The crude bash completion code for the 'doc' command:
```

_doc(){ [[ $COMP_CWORD -eq 1 && $2 == -* ]] && COMPREPLY=(--auto-redisplay);}
complete -W "`cd /usr/share/doc; echo *`" -F _doc doc

```

---

