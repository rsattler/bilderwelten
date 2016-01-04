Tipps zum Workflow
==================

Habe folgende Fenster offen, vielleicht sogar maximiert:

* Ein Explorer-Fenster, navigiert zum Repository, dem Ordner `rsattler.github.io`.
* Den Git-Client GitHub Desktop, zu finden im Startmenü.
* das Skript `serve`, gestartet durch Doppelklick im Repository-Ordner, für das Generieren der Vorschau.
* Ein Browserfenster, dirigiert zur Adresse `http://localhost:4000`, für die lokale Vorschau.

Grundinformationen zur Homepage
===============================

Git
---

Wir verwenden das Versionsverwaltungssystem Git zum Verwalten der Homepage.
Die Webseite wird kostenlos zentral gehostet von GitHub, die Adresse des Repositories ist <https://github.com/rsattler/rsattler.github.io>.

Um sich mit dem zentralen Repository zu verbinden, kann das Programm GitHub Desktop verwendet werden, zu finden im Startmenü.
Man synchronisiert zum Hochladen von vorgenommenen Commits oder um die lokale Version auf den aktüllen Stand zu bringen.
Der Button dafür befindet sich rechts oben.
Bevor Veränderungen durch Synchronisieren hochgeladen werden können, müssen sie erst in einen sogenannten Commit aufgenommen werden.
Hierzu wechselt man in die Ansicht "Changes", in der das Programm alle seit dem letzten Commit vorgenommene Veränderungen auflistet.
Man gibt eine kurze Zusammenfassung an, um die Zusammenarbeit mit anderen Editoren zu erleichtern, und klickt auf den Button "Commit".

Domain
------

Die sogennante Domain, der Hauptbestandteile der Adresse der Homepage, ist separat angemietet und ist `bilderwelten.regina-sattler.de`.
Um Git wissen zu lassen, unter welcher Adresse die Homepage erscheinen soll, beinhaltet die Datei CNAME im Repository den Domainnamen.
Separat ist die Domain in einem Benutzerkonto des Github-Benutzers `sattlerc` unter <http://www.inwx.de/> passend konfiguriert worden.

Aufbau
------

Typische Homepages bestehen aus vielen einzelnen HTML-Seiten, die zu grossen Teilen gleich aufgebaut (dasselbe Layout haben) sind und wiederkehrende Bausteine verwenden (z.B. das Menü oder der Titelblock).
Diese Bausteine wollen wir nicht immer wieder separat schreiben; nicht nur wegen der Mühe, sondern weil es das Verwalten und Aktualisieren der Homepage zum Alptraum macht (wenn wir nicht vorsichtig sind, könnte es nämlich passieren, dass wir das Menü aus versehen nur auf einigen Seiten ändern, was Besucher ziemlich verwirren würde).

Aus diesem Grund verwenden wir ein sogenanntes Template-System, Jekyll.
Dieses setzt auf die normale HTML-Sprache für Webseiten nochmal eine sogenannte Template-Sprache drauf, die es einem erlaubt, die Webseiten zu stückeln.
Bestandteile, die auf mehreren Seiten wiederverwertet werden sollen, kommen in den Unterorder `_includes`.
Layouts definieren mithilfe der Template-Sprache, wie sich Bestandteile zu vollständigen Seiten zusammensetzen; sie kommen in den Unterordner `_layouts`.

Die Inhalte der eigentlichen Seiten kommen in den Order selber, mit dem Namen unter dem sie später in der Adresszeile des Browsers auftauchen sollen.
Bevor die Webseite im Browser angezeigt wird, geht sie durch das Template-System, das dafür sorgt, dass die einzelnen Bestandteile wie mit den Template-Befehlen in den Dateien angegeben zusammengesetzt werden.
Dem Browsers erscheint jede Seite als einzelne Datei, in der keine Template-Befehle mehr vorkommen.

HTML
----

Hypertext Markup Language (abgekürzt HTML) ist die Sprache, in der Webseiten geschrieben werden.
Das Kernmerkmal sind sogennante Tags zum semantischen Strukturieren der Seite, z.B.
```
<title>Browserfenster-Titel</title>
```
zum Spezifizieren des Titels.
Tags können geschachtelt werden.
Für Einführung und Referenz zu HTML siehe:

* <http://www.w3schools.com/html/default.asp>
* <http://www.w3schools.com/tags/default.asp>

CSS
---

Cascading Style Sheets (akgekürzt CSS) definieren das Aussehen einer Webseite.
Hier wird festgelegt, welche Schriftart für welche Seitenelemente zu verwenden ist, wie groß Elemente sind und wie sie positioniert werden sollen, welche Ränder sie haben sollen, wie die farbliche Gestaltung aussehen soll, wie der Hintergrund aussehen soll, etc.
Für Einführung und Referenz zu HTML siehe:

* <http://www.w3schools.com/css/default.asp>
* <http://www.w3schools.com/cssref/default.asp>

Template-Befehle (Jekyll)
-------------------------

Innerhalb aller HTML-Dateien können Template-Befehle verwendet werden, zum Beispiel um andere HTML-Bausteine einzubinden.
Diese haben die Form `{% ... %}`, zum Beispiel
```
{% include menu.html %}
```
zum Einbinden des Menüs.
Für Informationen zu zum Template-System Jekyll/Liquid siehe:

* <https://docs.shopify.com/themes/liquid-documentation/basics>
* <https://github.com/Shopify/liquid/wiki>
* <http://jekyllrb.com/docs/variables/>

Wie erstelle ich eine neue Seite?
---------------------------------

Lege eine HTML-Datei wie zum Beispiel page-name.html im Ordner an.
Der Dateiname ist später nur revelant für die Adressezeile des Browser
Die ersten Zeilen sollten wie folgt aussehen:
```
---
layout: default
menu-weight: 1
menu-title: Seitenname
---
```
Der Eintrag `layout` gibt dem Template-System die Information, mit welchem Layout die Seite zusammengesetzt werden soll, in diesem Fall das Default-Layout, zu finden in `_layout/default.html`.
Der Eintrag `menu-weight` gibt an, wo die Seite im Menü stehen soll; Seiten mit niedrigerem Gewicht stehen weiter vorne als Seiten mit höherem Gewicht.
Der Eintrag `menu-title` git an, wie die Seite im Menü heißen soll
Wenn die Seite nicht im Menü auftauchen soll, müssen die letzten beiden Zeilen gelöscht werden.
Nach diesen Template-Befehlen geht der eigentliche HTML-Seiteninhalt los.

Wie editiere ich eine Datei mit Notepad++?
------------------------------------------

1. Rechtsklicken.
2. Edit with Notepad++.

Wie schaue ich die Homepage lokal vor?
--------------------------------------

1. Doppelklicken auf `serve`.
2. Konsolenfenster so lange auflassen, wie man die Homepage testen möchte.
3. Im Browser folgende Adresse öffnen: `http://localhost:4000/`
4. Änderungen an den Homepage-Dateien werden sofort übernommen solange das Konsolenfenster offen ist.
   Lediglich die Seite im Browser muss aktualisiert werden.


Bedeutungen der einzelnen Dateien und Unterordner
=================================================

_includes
--------

Dieser Unterordner enthält wiederverwertbare HTML-Bausteine, die in einzelnen Seiten Verwendung finden können.
Momentan sind dies die folgenden Dateien:

* `_includes/head.html`: Meta-Informationen der Homepage, z.B. Browserfenster-Titel, Stylesheets.
* `_includes/header.html`: Überschriftenblock, der über dem Menü erscheint.
* `_includes/menu.html`: Das Seitenmenü.
* `_includes/footer.html`: Fußzeile, enthält z.B. Änderungsdatum, Link zu Disclaimer, Impressum.

_layouts
--------

Dieser Unterordner enthält skelettartige HTML-Dateien mit Template-Befehlen, die diktieren, wie Seiten zusammengesetzt werden sollen.
Momentan gibt es nur das Default-Layout `_layouts/default.html`;

_site
-----

Dieser Unterordner enthält die mit `serve` lokal generierte Testversion der Homepage zum Voranschauen.
Kann ignoriert werden und gehört nicht zum Repository.

css
---

In diesem Unterordner liegen sogenannte Style-Sheets.
Sie definieren, wie die Webseiten der Homepage aussehen sollen.
Dies folgt dem Prinzip der Trennung von Inhalt und Aussehen: Inhalt wird allein in den HTML-Dateien definiert, während das Aussehen (Positionierung, Formatierung, etc.) in den CSS-Dateien definiert ist.

Images
------

In diesen Unterordner legen wir alle (möglicherweise später) zu verwendenden Bilddateien hinein.
Wenn ein Bild zum Beispiel den Pfad `Images/foto.jpg` hat, dann kann es in HTML-Dateien wie folgt eingebunden werden:
```
<img src="Images/foto.jpg">
```
serve.cmd
---------

Ein kleines Skript um eine Testversion der Homepage lokal zu generieren.
Die Ausgabe ist der Unterordner `_site`.
Für Benutzung, siehe Abschnitt: "Wie schaue ich die Homepage lokal vor?"
Sollte nicht verändert werden.

robots.txt
----------

Solange diese Datei mit ihrem Inhalt existiert, werden Suchmaschinen beim Lesen der Homepage abgewiesen.
Muss gelöscht werden, wenn die Homepage per Suchmaschine auffindbar gemacht werden soll.

CNAME
-----

Die gemietete Domain, unter der die Homepage angezeigt werden soll.
Sollte nicht verändert werden.

.gitignore
----------

Die Datei enthält eine Liste von Pfaden die von Git ignoriert werden soll.
Diese Pfade gehören nicht zum Repository und werden somit nicht synchronisiert, obwohl sie im Ordner liegen.
Dies ist sinnvoll für temporäre Dateien wie zum Beispiel die lokal mit `serve` generierte Testseite im Unterordner `_site`.
Sollte normalerweise nicht verändert werden.

README.md
---------

Diese Hilfe.
