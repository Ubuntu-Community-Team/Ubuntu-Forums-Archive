---
title: "Ubuntu Server YAML Validation via shell"
date: 2018-04-18
forum: Server Platforms
---

### Post by LHammonds on 2018-04-18
With the need to use YAML in Ubuntu Server 18 (netplan), is there a built-in way to validate a .yaml file BEFORE it blows up inside whatever app is trying to use it?

I've found various online validators and other ways using Python, Ruby and travis but I'm looking for a way to validate without the need to install additional software.

I thought about making a wrapper to feed a file to an online service but  if the service goes away or do not have Internet access, it would be  wasted effort. (**EDIT**: This might be the only way if nothing built-in works)

Anyone have a solution?

Thanks,
LHammonds

EDIT: Stuff I've found so far related to this

[Bash script to read YAML using sed/awk](https://gist.github.com/pkuczynski/8665367) (by pkuczynski)
[Bash script expanding pkuczynski script](https://github.com/jasperes/bash-yaml) (by jasperes)
[Verify YAML via Shell](https://liquidat.wordpress.com/2016/01/21/short-tip-verify-yaml-in-shell-via-python-one-liner/) (requires Python)
[yamllint.com](http://www.yamllint.com/) - Online web-based validator
[CodeBeautify.org](https://codebeautify.org/yaml-validator) - Online web-based validator

---

