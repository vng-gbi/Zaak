# Foutoplossing

Nadat een bestand in een op de VNG-R-Respec-Temp[late repository gebaseerde repository wordt gewijzigd, toegevoegd of verwijderd treedt het 'Build' action script in werking. Er kunnen zich daarbij diverse problemen voordoen.
Detectie van een probleem start altijd bij het onderzoeken van de Action workflows. Deze kun je benaderen door in GitHub het tabblad 'Actions' aan te klikken waarn. In het daarop volgende scherm tref je vervolgens een tweetal typen workflows aan.

* Update workflows
* pages build en deployment workflows

Het eerste type draagt over het algemeen de naam van een gewijzigd bestand en dit zal over het algemeen het type workflow zijn waarin zich de problemen voordoen. Om beter te kunnen bepalen wat er precies fout ging moet je op de workflow klikken.
In het daarop volgende menu kun je de uitegevoerde modules zien en waar het fout is gegaan, ook daar kun je weer op klikken. Tenslotte kun je daar weer de foutgelopen stap zien
Ter ondersteuning bij het oplossen van die problemen beschrijven we er hier een aantal en geven we aan wat daar de mogelijke oorzaak van is en hoe je dat kunt oplossen.

| Foutgelopen module | Foutieve job | Probleem | Mogelijke oorzaak | Oplossing |
| --- | --- | --- | --- | --- |
| Check/Links | Check links | Er worden één of meer links getoond met http 404 codes. | De betreffende link komt voor in het aangegeven bestand. Veelal het gegenereerde snapshot.html bestand. | <li>Het kan een in het document voorkomende url betreffen die niet echt correct hoeft te zijn. In dat geval kun je hem negeren.</li><li>Betreft het de link die vermeldt staat bij 'Deze versie', 'Laatst gepubliceerde versie', 'Laatste werkversie' of 'Vorige versie' dan moet je checken of de url wel overeenkomt met een in de publicatie repository geplaatste versie of met de url van de GitHub Pages van de Respec repository zelf. Corrigeer evt. de publicatie repository.</li> |
| Check/Links | Build/HTML | De job zelf lijkt goed te gaan want deze is groen maar in een van de stappen komt een error voor.| Het probleem kan vele oorzaken hebben. De foutmelding ziet er als volgt uit:</br><img align="left" width="100" height="100" src="./media/Foutmelding2.png"> | Open de gegenereerde GitHub Pages pagina en druk op F12. In de console view wordt de javascript error getoond. Deze kan je mogelijk verder brengen. |
| Check/Links | Build/HTML | De job zelf lijkt goed te gaan want deze is groen maar in een van de stappen komt een error voor.| In een of meer markdown of html bestanden komt meer dan één `dfn` element voor met een gelijke inhoud. De foutmelding ziet er als volgt uit:</br><img align="left" width="100" height="100" src="./media/Foutmelding3.png"> | Zorg er voor dat er geen duplicaat `dfn` elementen meer voorkomen. |
| Check/Links | Build/HTML | De job zelf lijkt goed te gaan want deze is groen maar in een van de stappen komt een error voor.| In een of meer markdown of html bestanden komt meer dan één `dfn` element voor met een gelijke waarde voor het `data-lt` attribuut. De foutmelding ziet er als volgt uit:</br><img align="left" width="100" height="100" src="./media/Foutmelding4.png"> | Zorg er voor dat er geen twee of meer `dfn` elementen voorkomen met een gelijke waarde voor het `data-lt` attribuut. |
| Check/WCAG | Run pa11y snapshot.html | Er zijn een of meerdere fouten gedetecteerd die tegen de WCAG principes in gaan | Mogelijk heb je een fout gemaakt in de html of je hebt in html een constructie gebruikt die niet gewenst is. De foutmelding ziet er vaak als volgt uit:<br/><img align="left" width="100" height="100" src="./media/Foutmelding1.png"> | Met het deel achter `WCAG2AA.` bijv. `Principle1.Guideline1_3.1_3_1.H49.AlignAttr` kun je over het algemeen op internet (bijv. op https://squizlabs.github.io/HTML_CodeSniffer/Standards/WCAG2/) opzoeken wat het probleem is. |
| Check/Links | Build/HTML | De job zelf lijkt goed te gaan want deze is groen maar in een van de stappen komt een error voor en het Respec document toont niet de door Imvertor gegenereerde content.| Het voor het imvertor gegenereerde resultaat in het 'index.html' geplaatste `section` element heeft een foutieve waarde voor het `data-include-format` attribuut. | Wijzig de waarde `md` in `html`. |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
