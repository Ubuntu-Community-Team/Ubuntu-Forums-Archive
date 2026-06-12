---
title: "Transelation needed"
date: 2008-05-03
forum: The Cafe
---

### Post by Martje_001 on 2008-05-03
Hello,
I wish to translate this into as many languages as possible. Can you help me?

**English:**
```
yes="yes"
no="no"
supported_distros="Currently this script supports:

1) Debian Sid (gnome)
2) Debian Sid (kde)
3) Debian Lenny (gnome)
4) Debian Lenny (kde)
5) Ubuntu Gutsy (gnome)
6) Kubuntu Gutsy (kde)
7) Ubuntu Hardy (gnome)"
dis_specified="Distribution specified in configurationfile, following."
done="done!"
failed="failed!"
get_git1="Pulling" # Example: Pulling compiz from git
get_git2="from git... " # Example: Pulling compiz from git
nothing_changed="No settings changed, skipping question."
not_root="You're not root. Is it ok to use sudo command? ($yes/$no): "
pick_supported_distros="Please pick a distribution (number): "
repo_t="Found 1 repo, autoselecting 'annongit.opencompositing.org'."
save_settings="Save settings? ($yes/$no): "
config_run_root="Configuration-file says to not use sudo. Please run this script as root."
config_sudo="Configuration-file says to use sudo, following."
error1="You should run this script with either the install option or the uninstall option.
Example: ./compiz-git install"
uninstall_mess="Uninstalling.. "

```

**Dutch:**
```
yes="ja"
no="nee"
supported_distros="Op het moment ondersteunt het script de volgende distributies:

1) Debian Sid (gnome)
2) Debian Sid (kde)
3) Debian Lenny (gnome)
4) Debian Lenny (kde)
5) Ubuntu Gutsy (gnome)
6) Kubuntu Gutsy (kde)
7) Ubuntu Hardy (gnome)"
dis_specified="Distributie aangegeven in configuratiebestand, volgen."
done="klaar!"
failed="mislukt!"
get_git1="Bezig met ophalen van" # Example: Pulling compiz from git
get_git2="van git... " # Example: Pulling compiz from git
nothing_changed="Geen instellingen veranderen veranderdt, vraag overslaan."
not_root="U bent geen root, is het goed dat het sudo commando wordt gebruikt? ($yes/$no): "
pick_supported_distros="Kies een distributie (nummer): "
repo_t="1 bronnenlijst gevonden, automatisch selecteren van 'annongit.opencompositing.org'."
save_settings="Instelling opslaan? ($yes/$no): "
config_run_root="Configuratiebestand zegt dat er geen sudo-commando gebruikt mag worden. Draai dit script alstublieft als root."
config_sudo="Configuratiebestand zeg dat sudo gebruikt mag worden, volgen."
error1="Dit script moet met de optie "install" of "uninstall" worden gebruikt.
Voorbeeld: ./compiz-git install"

```

I'm sorry if it is a bit unclear here on the forums ;). Thank you!

---

### Post by alarme on 2008-05-03
yes="si"
no="no"
distribuciones soportadas="Actualmente este script soporta:

1) Debian Sid (gnome)
2) Debian Sid (kde)
3) Debian Lenny (gnome)
4) Debian Lenny (kde)
5) Ubuntu Gutsy (gnome)
6) Kubuntu Gutsy (kde)
7) Ubuntu Hardy (gnome)"
dis_specified="Distribución especificada en el archivo de configuración, continuando."
done="¡Hecho!"
failed="¡Falló!"
get_git1="Descargando" # Ejemplo: Descargando compiz desde git
get_git2="desde git... " # Ejemplo: Descargando compiz desde git
nothing_changed="No se han modificado los ajustes, saltando la pregunta."
not_root="Usted no es root. ¿Usar la orden sudo? ($si/$no): "
pick_supported_distros="Por favor, seleccione una distribución (número): "
repo_t="Encontrado 1 repositorio, autoseleccionando 'annongit.opencompositing.org'."
repo_t="Encontrados 2 repositorios, autoseleccionando 'annongit.opencompositing.org'."
repo_t="Encontrado(s) 1 repositorio(s), autoseleccionando 'annongit.opencompositing.org'."
save_settings="¿Guardar ajustes? ($si/$no): "
config_run_root="El archivo de configuración no permite usar sudo. Por favor, ejecute este script como root."
config_sudo="El archivo de configuración permite usar sudo, continuando."
error1="Debe ejecutar este script con las opciones instalar o desinstalar.
Ejemplo: ./compiz-git instalar"
uninstall_mess="Desinstalando.. "

---

### Post by Martje_001 on 2008-05-04
This is Spanish? Also, can you give me the output of 'echo $LANG' to see your country code?

---

### Post by alarme on 2008-05-04
es_ES.UTF-8

---

### Post by billgoldberg on 2008-05-04
I would help, but I see you already have the dutch translation nailed.

Although there seems to be an error here:

Geen instellingen veranderen veranderdt, vraag overslaan.

That should be this:

Geen instellingen veranderd, vraag overslaan.

Verander**dt** is a huge grammatical mistake.

Also:

"U bent geen root, is het goed dat het sudo commando wordt gebruikt?"

I think it would be better if you use this:

"U bent geen root, mag het sudu commando gebruikt worden?"

It reads a bit better.

Another remark.

You use "sudo commando" in one sentence and in another you use "sudo-commando". 

I don't believe you need the "-" between those words.

But I'm not 100% sure "commando" is the right word to use.

And one final remark.

The phrase "draai het script als root", seems a bit weird to use.

Wouldn't this be better put like this: "Start het script ..." or "Open het script ..."?

edit:

Shouldn't it be "Op dit moment ..." instead of "Op het moment ..."?

---

### Post by Martje_001 on 2008-05-04
Aah, Nederlands is mijn favoriete vak, zoals je ziet :). En ik ben nog Nederlander ook..

But, thank you for your corrections!

---

