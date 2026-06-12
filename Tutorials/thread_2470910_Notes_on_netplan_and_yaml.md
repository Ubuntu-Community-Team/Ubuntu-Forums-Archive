---
title: "Notes on netplan and yaml"
date: 2022-01-16
forum: Tutorials
---

### Post by The Cog on 2022-01-16
I see a number of posts by people having trouble with netplan, and its yaml format. So I made a few notes that I hope people might find useful:

YAML (Yet Another Markup Language) is a language designed for representing data. It is very flexible, and has many options on how to represent data, which can cause confusion. I have adopted a recent posting of a netplan configuration and simply printed it in a number of different ways, to highlight and maybe explain some of the causes of confusion. Here is the original netplan file content:
```
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    eth0:
      addresses:
        - 192.168.8.100/24
      dhcp4: false
      dhcp6: false
      gateway4: 192.168.8.1
      nameservers:
          addresses: [ 8.8.8.8, 8.8.4.4 ]
    eno1:
      addresses:
        - 192.168.9.100/24
      dhcp4: false
      dhcp6: false
      gateway4: 192.168.9.1
      nameservers:
          addresses: [ 8.8.8.8, 8.8.4.4 ]

```
This shows lists of addresses in two different ways, which can be confusing. Both ways of representing lists are valid: either enclosed in brackets and separated by commas (the nameserver addresses), or one per line, introduced by a dash which signifies it is a list element.
I used a python library to print that network description in slightly different formats. First, read the file in. Ignore the "unsafe" warning, but this method can be used as a way of verifying that a file contains valid yaml text (my typing is in red): Every one of the representations I show below is equally valid to mean the **same thing** in a netplan file:
```
~$ [COLOR="#FF0000"]python3[/COLOR]
Python 3.8.10 (default, Nov 26 2021, 20:14:08) 
[GCC 9.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import yaml, json
>>> [COLOR="#FF0000"]net = yaml.load(open("netplan.yml"))[/COLOR]
<stdin>:1: YAMLLoadWarning: calling yaml.load() without Loader=... is deprecated, as the default Loader is unsafe. Please read [https://msg.pyyaml.org/load](https://msg.pyyaml.org/load) for full details.
```
The python yaml library's default way of printing it is like this. Notice the way it likes to display lists one element per line:
```
>>> [COLOR="#FF0000"]print(yaml.dump(net))[/COLOR]
network:
  ethernets:
    eno1:
      addresses:
      - 192.168.9.100/24
      dhcp4: false
      dhcp6: false
      gateway4: 192.168.9.1
      nameservers:
        addresses:
        - 8.8.8.8
        - 8.8.4.4
    eth0:
      addresses:
      - 192.168.8.100/24
      dhcp4: false
      dhcp6: false
      gateway4: 192.168.8.1
      nameservers:
        addresses:
        - 8.8.8.8
        - 8.8.4.4
  renderer: NetworkManager
  version: 2

```
Or we can tell it to print items on one line if possible in which case the interface addresses are also shown in a bracketed list of one item:
```
>>> [COLOR="#FF0000"]print(yaml.dump(net, default_flow_style=None))[/COLOR]
network:
  ethernets:
    eno1:
      addresses: [192.168.9.100/24]
      dhcp4: false
      dhcp6: false
      gateway4: 192.168.9.1
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
    eth0:
      addresses: [192.168.8.100/24]
      dhcp4: false
      dhcp6: false
      gateway4: 192.168.8.1
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
  renderer: NetworkManager
  version: 2

```
I personally find the above the most readable format, perhaps because I have understood that use of brackets to mean a list for many years. 
The indentation is critical because it indicates that an item is a member/property of something else the next level out., I.e. ethernets, renderer and version are all named properties of network. Similarly, eno1 and eth0 are named properties of ethernets. Note that named properties don't have an implied sort order - they are not lists, just a collection of properties.
The YAML specification requires using spaces and not tabs for indentation, although some implementations of YAML readers do accept tabs (the python library seems to treat a tab as 8 spaces).

This is yaml's most compressed form, which is harder to read because it just splits the text to keep the width within reason. The thing to note here is that a list of properties for something is denoted by braces {} instead of having to be equally indented one per line:
```
>>> [COLOR="#FF0000"]print(yaml.dump(net, default_flow_style=True))[/COLOR]
{network: {ethernets: {eno1: {addresses: [192.168.8.100/24], dhcp4: false, dhcp6: false,
        gateway4: 192.168.8.1, nameservers: {addresses: [8.8.8.8, 8.8.4.4]}}, eth0: {
        addresses: [192.168.8.100/24], dhcp4: false, dhcp6: false, gateway4: 192.168.8.1,
        nameservers: {addresses: [8.8.8.8, 8.8.4.4]}}}, renderer: NetworkManager,
    version: 2}}

```

JSON is another popular data representation format, and it happens to be a subset of YAML.
JSON requires text strings to be quoted whereas YAML just knows when text is text (although you would have to put something that looks like a number in quotes, e.g. with 42 and "42", the first is a numeric value).
JSON always requires braces {} to denote a set of named properties. Any indentation is optional and just for human readers' convenience.
JSON always uses brackets [] to denote lists
JSON does not allow comment lines (line breaks are not significant in JSON)
So below, just for interest, is the same network description in JSON. It would work just fine in a netplan file because it is also valid YAML. 
If you then removed all the quotes it would still be valid YAML.
You could remove either the braces or the indentation (not both) and it would still mean the same thing in YAML.
Schragge points out that a space after the colon is required in YAML but not in JSON. I would always type a space there by habit, so hadn't noticed the difference.
```
>>> [COLOR="#FF0000"]print(json.dumps(net, indent=2))[/COLOR]
{
  "network": {
    "version": 2,
    "renderer": "NetworkManager",
    "ethernets": {
      "eth0": {
        "addresses": [
          "192.168.8.100/24"
        ],
        "dhcp4": false,
        "dhcp6": false,
        "gateway4": "192.168.8.1",
        "nameservers": {
          "addresses": [
            "8.8.8.8",
            "8.8.4.4"
          ]
        }
      },
      "eno1": {
        "addresses": [
          "192.168.9.100/24"
        ],
        "dhcp4": false,
        "dhcp6": false,
        "gateway4": "192.168.9.1",
        "nameservers": {
          "addresses": [
            "8.8.8.8",
            "8.8.4.4"
          ]
        }
      }
    }
  }
}

```

---

### Post by TheFu on 2022-01-16
> The YAML specification requires using spaces and not tabs for indentation

This is key.

Also, when posting in these forums, using code-tags is the best way to retain the indentation.
Code-tags how-to: [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)

---

### Post by schragge on 2022-01-16
Also, the space after the colon is significant in YAML, but isn't in JSON.

Both [FONT=monospace]"dhcp4":false,[/FONT] and [FONT=monospace]"dhcp4": false,[/FONT] are valid in JSON.

OTOH, the only valid YAML is [FONT=monospace]dhcp4: false[/FONT]

---

### Post by The Cog on 2022-01-17
> **schragge said:**
> Also, the space after the colon is significant in YAML, but isn't in JSON.

Both [FONT=monospace]"dhcp4":false,[/FONT] and [FONT=monospace]"dhcp4": false,[/FONT] are valid in JSON.

OTOH, the only valid YAML is [FONT=monospace]dhcp4: false[/FONT]
Is it really? Hah! Evan after using YAML for years I had not noticed (or remembered) that. Clearly I am simply in the habit of typing a space after a colon without even thinking about it.
Thanks for that.

---

### Post by schragge on 2022-01-17
It's in [the spec]("http://yaml.org/spec/1.2.2/#collections"):
> YAML’s [block collections]("http://yaml.org/spec/1.2.2/#block-collection-styles") use [indentation]("http://yaml.org/spec/1.2.2/#indentation-spaces") for scope and begin each entry on its own line. [Block sequences]("http://yaml.org/spec/1.2.2/#block-sequences") indicate each entry with a dash and space (“[highlight][font=monspace]- [/font][/highlight]”). [Mappings]("http://yaml.org/spec/1.2.2/#mapping") use a colon and space (“[highlight][font=monspace]: [/font][/highlight]”) to mark each [key/value pair]("http://yaml.org/spec/1.2.2/#mapping"). [Comments]("http://yaml.org/spec/1.2.2/#comments") begin with an octothorpe (also called a “hash”, “sharp”, “pound” or “number sign” - “[highlight][font=monspace]#[/font][/highlight]”).

---

### Post by kevdog on 2022-01-17
Do you know of a good yaml linter?

---

### Post by DuckHook on 2022-01-17
*Thread useful enough to move to: **Tutorials***

---

### Post by schragge on 2022-01-17
> **kevdog said:**
> Do you know of a good yaml linter?
Don't know how good it is, but there's [validyaml]("https://github.com/martinlindhe/validyaml").

Actually, I suppose most of the tools mentioned @[https://github.com/dbohdan/structured-text-tools#yaml-toml](https://github.com/dbohdan/structured-text-tools#yaml-toml) may be useful in this regard.

---

### Post by The Cog on 2022-01-18
> **kevdog said:**
> Do you know of a good yaml linter?
yamllint is in the repo
> Description: Linter for YAML files
 yamllint does not only check for syntax validity, but for weirdnesses like
 key repetition and cosmetic problems such as lines length, trailing
 spaces, indentation, etc.

---

