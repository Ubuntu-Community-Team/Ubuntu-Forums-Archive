---
title: "[SOLUCIONADO] openoffice en ingles"
date: 2009-06-18
forum: Software
---

### Post by zhelo on 2009-06-18
resulta que cuando instale ubuntu, creo que venia con este programa en español
el asunto es que ahora lo tengo ej ingles, ademas que cuando una palabra la escribo mal las palabras parecidas son solo en ingles,
queria saber como hago para ponerlo en español??

---

### Post by radixs on 2009-06-18
> **zhelo said:**
> resulta que cuando instale ubuntu, creo que venia con este programa en español
el asunto es que ahora lo tengo ej ingles, ademas que cuando una palabra la escribo mal las palabras parecidas son solo en ingles,
queria saber como hago para ponerlo en español??

Entra a synaptic y busca el paquete español de openoffice y lo instalas ;)

---

### Post by G3R-4 on 2009-06-18
> **zhelo said:**
> resulta que cuando instale ubuntu, creo que venia con este programa en español
el asunto es que ahora lo tengo ej ingles, ademas que cuando una palabra la escribo mal las palabras parecidas son solo en ingles,
queria saber como hago para ponerlo en español??


zhelo, haz lo siguiente:

Sistema - Administración - Gestor de paquetes Synaptic

En "buscar" escribe: openoffice

Marca para instalar (clic derecho marcar para instalar) todos los paquetes que terminen en -es (de Español) y marcas para desinstalar los paquetes terminados en -en (de English).

 Espero se entienda.-

Atte.
G3R-4

---

### Post by zhelo on 2009-06-18
> **G3R-4 said:**
> zhelo, haz lo siguiente:

Sistema - Administración - Gestor de paquetes Synaptic

En "buscar" escribe: openoffice

Marca para instalar (clic derecho marcar para instalar) todos los paquetes que terminen en -es (de Español) y marcas para desinstalar los paquetes terminados en -en (de English).

 Espero se entienda.-

Atte.
G3R-4

no me aparece nada de -es

---

### Post by CdK1 on 2009-06-18
Mira esto:

Caturra:/home/CdK1# apt-cache search openoffice | grep esp
libxml-java-openoffice.org - namespace aware SAX-Parser utility library (OOo 3.1 branch)
myspell-eo - Diccionario de esperanto para myspell
myspell-es - Diccionario de español para myspell
openoffice.org-help-es - Paquete completo de productividad ofimática, ayuda en español
openoffice.org-l10n-es - Paquete completo de productividad ofimática, paquete del idioma español
Caturra:/home/CdK1# 

Como te dije anteriormente man apt-get ;)

---

### Post by radixs on 2009-06-19
hay... tan simple como buscar en synaptic este paquete

openoffice.org-l10n-es

---

### Post by 3nG3ndR0 on 2009-06-19
Como dice @Cdk1 y @radixs solo hay escribir en el terminal lo siguiente:

openoffice.org-l10n-es - Paquete completo de productividad ofimática, paquete del idioma español

```
sudo aptitude install openoffice.org-l10n-es
```myspell-es - Diccionario de español para myspell

```
sudo aptitude install myspell-es
```

---

### Post by zhelo on 2009-06-19
> **radixs said:**
> hay... tan simple como buscar en synaptic este paquete

openoffice.org-l10n-es

gracias compañero, funco la wea
tema solucionado

---

### Post by nopersona on 2009-06-19
> **zhelo said:**
> gracias compañero, funco la wea
tema solucionado

Moderemos el lenguaje, por favor ;)

---

### Post by ppellet on 2009-07-01
> **3nG3ndR0 said:**
> Como dice @Cdk1 y @radixs solo hay escribir en el terminal lo siguiente:

openoffice.org-l10n-es - Paquete completo de productividad ofimática, paquete del idioma español

```
sudo aptitude install openoffice.org-l10n-es
```myspell-es - Diccionario de español para myspell

```
sudo aptitude install myspell-es
```



¡Excelente!

Tenía un problema similar. Instalé Ubuntu 8.04, pero la ofimática quedó en inglés, en realidad, sólo la interfaz del usuario.

Seguí estas instrucciones y a mí también me... (funcó, jajaja que lenguaje)

Saludos,:guitar:

---

### Post by zhelo on 2009-07-01
si yo lo formatee uy esto me ayudo caleta

---

