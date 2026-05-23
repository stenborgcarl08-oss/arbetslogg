# Lanseringsplan v2 — Partner-utgåva

**Datum:** 2026-05-23
**Status:** Designspec, ej implementerad
**Ersätter:** `Lanseringsplan_Checklista.html` (befintlig v1)

---

## Sammanhang

Mobil Bilvård Åland drivs nu av **Calle Stenborg och Hugo (50/50)** — inte längre som enskild näringsidkare. Den befintliga lanseringsplanen (35 tasks i 5 faser) är skriven för en ensam grundare och saknar tre kritiska områden:

1. **Bolagsform och partnerjuridik** — enskild näringsidkare är inte möjligt med två jämbördiga ägare.
2. **Miljölagstiftning på Åland** — smutsvatten/produktvatten från biltvätt får inte hamna i dagvattenbrunnar.
3. **Utrustning för vattenhantering** — DIY-byggd uppsamlingsmatta som tekniskt och ekonomiskt enklare alternativ till installerad oljeavskiljare.

Detta dokument specar version 2 av planen.

---

## Mål

En självständig HTML-fil som:

- Behåller befintlig Apple-Swiss dark/guld-stil och interaktiva mekanik (sticky progress, localStorage, confetti).
- Lägger till en **Fas 0: Grundläggning** överst med juridik, miljö och utrustning.
- Innehåller en utfällbar **byggguide för vattenmatta** inbäddad direkt i den relevanta uppgiften.
- Är skriven för **två personer som arbetar tillsammans** — ingen uppdelning av ansvar.
- Kan användas på mobil i fält.

---

## Filstruktur

| Fil | Åtgärd |
|---|---|
| `Lanseringsplan_Checklista.html` | **Skrivs över.** Git bevarar v1 i historiken. |
| Övriga filer | Orörda. |

Inga nya filer eller mappar skapas. CSS, JS och HTML hålls samlat i den enda filen, precis som v1.

---

## Innehållsstruktur

### Fas 0 — Grundläggning (NY, läggs överst)

Tagg: orange "Fas 0 — Grund" (distinkt från Fas 1:s röda urgent-tagg). Samtliga uppgifter markerade som kritiska (röd vänsterkant — den per-task-markeringen är ett separat visuellt element från fas-taggen och de krockar inte).

| # | Uppgift | Notering |
|---|---|---|
| 0.1 | Välj bolagsform (öppet bolag eller Ab) | Båda måste vara överens. Default-rekommendation: öppet bolag. |
| 0.2 | Registrera bolaget hos PRH (FO-nummer) | Kräver bolagsavtal + e-identifiering. ~50–380 € beroende på form. |
| 0.3 | Skriv partneravtal Calle/Hugo | Vinstdelning 50/50, ansvar, utträdesvillkor. Mall finns hos PRH. |
| 0.4 | Teckna företagsförsäkring (ansvar + egendom) | Kritisk — verksamhet med andras dyra bilar. |
| 0.5 | Lös vattenhanteringen | Innehåller utfällbar byggguide (se nedan). |
| 0.6 | Verifiera lagligt hos ÅMHM | Få skriftligt OK på vattenlösningen innan första jobbet. |
| 0.7 | Anmälan till skatteförvaltningen (moms, förskottsuppbörd) | Direkt efter bolagsregistrering. |
| 0.8 | Öppna gemensamt företagskonto | För bolagets in- och utbetalningar. |
| 0.9 | Bestäm intern arbetsrytm | Inte ansvarsuppdelning — snarare hur ni planerar veckan, vem som tar bokningssamtalet vid en given tid, etc. |

### Faser 1–5 (uppdateras från v1)

- Alla "jag"/"du"-formuleringar skrivs om till "vi".
- Genomgång för att hitta tasks som inte längre är relevanta eller dubbleras av Fas 0 (t.ex. avsnitt om enskild firma).
- Tasks ordning och innehåll bevaras i övrigt — formatet är välfungerande.

### Byggguide för vattenmatta (accordeon inuti task 0.5)

Kollapsbar sektion. Klick på pil fäller ut.

**A. Materiallista (bockbar)**
- PVC-presenning 5×6 m, ca 500 g/m² (~80–100 €)
- 4 st skumkorvar / pool noodles (~10–20 €)
- Värmepistol (låna om möjligt)
- PVC-lim/tejp som backup
- Liten dränkbar pump + 25 L dunk
- **Budgetmål: under 200 €**

**B. Mått och motivering**
- 5×6 m = täcker personbil med ~50 cm marginal
- Bilen ska kunna köras på mattan utan att förskjuta korven

**C. Byggsteg (numrerade, bockbara)**
1. Klipp PVC till mått, lämna 15 cm i varje ände för fickan
2. Vik 15 cm-änden inåt → bildar ficktunneln
3. Värmesvetsa kanten (eller limma med PVC-lim) — testa på en bit först
4. Trä in skumkorvar i fickan
5. Testa med vatten på plan, hård yta — kontrollera att inget läcker över kanten
6. Testa att köra in och ut med en bil utan att korven flyttar sig

**D. Vad som händer efter tvätten (kritiskt)**
1. Pumpa upp vattnet från mattan till dunken
2. Transportera till godkänd mottagning (avtalat med ÅMHM i task 0.6)
3. Skölj mattan, rulla ihop, transportera

Den här delen markeras tydligt visuellt — utan plan för var vattnet **tar vägen** är verksamheten inte laglig.

---

## Visuell stil och interaktion

Återanvänder befintligt CSS-system från v1:

- Färgvariabler (`--bg`, `--gold`, `--green`, `--red`, etc.)
- Phase-tag-systemet (utökas med en `phase-tag.foundation` i orange `#ff9f0a` — färgen finns redan i v1:s confetti-palett och är visuellt distinkt från Fas 1:s röda "urgent"-tagg)
- Task-format med kritisk-markör (röd vänsterkant)
- Sticky header med procent-progress och fasprogress
- localStorage-state per task-id (befintlig nyckel `mba_launch_v1` byts till `mba_launch_v2` för att inte krocka med gamla bockar)
- Confetti vid bock, reset-knapp, mobiloptimerat

**Nytt CSS för accordeon:**
- `<details>` + `<summary>` (native HTML, inget JS-behov)
- Stylad med samma kort-radius och gold-line som befintliga task-kort
- Sub-tasks inuti accordeon använder samma `.task`-klass som övriga

**Ny intro-text** överst i Fas 0 (1 mening): "Vi delar inte upp uppgifter — allt görs tillsammans."

---

## Tekniska val

| Val | Beslut | Motivering |
|---|---|---|
| Bibliotek | Inga | Konsistens med projektets HTML/CSS-stack (CLAUDE.md). |
| Accordeon | Native `<details>`/`<summary>` | Behöver inget JS, fungerar offline, tillgängligt. |
| Ägar-tags | Skippas | Alla tasks är "båda" — taggar tillför endast visuellt brus. |
| Filter ("visa mina") | Skippas | Inget värde utan ägar-tags. |
| Material för matta | PVC | Användaren vill värmesvetsa fickor; EPDM kan inte värmesvetsas. |
| localStorage-nyckel | `mba_launch_v2` | Undviker krock med gamla v1-bockar. |
| Filnamn | `Lanseringsplan_Checklista.html` (oförändrat) | Git bevarar v1 i historiken. |

---

## Vad detta dokument INTE löser

För tydlighet — detta är scope av v2-planen:

- Brain.md uppdateras INTE i detta arbete. Den behöver också uppdateras (Team-sektionen + bolagsform), men görs separat.
- Hemsidan (index.html) uppdateras INTE här (t.ex. "vi" istället för "jag" i texterna).
- Faktiskt val av bolagsform görs INTE här — det är en av uppgifterna **i** planen.
- Konkreta leverantörer för PVC-presenning, försäkring etc. researchas INTE här — det är också uppgifter i planen.

---

## Acceptanskriterier

Planen är klar när:

1. Filen `Lanseringsplan_Checklista.html` är överskriven med v2-innehållet.
2. Fas 0 visas överst med alla 9 uppgifter och korrekt röd "Grund"-tagg.
3. Task 0.5 har en utfällbar byggguide som fungerar utan JavaScript.
4. Befintliga faser 1–5 är omformulerade till "vi" och dubbleringar mot Fas 0 är borttagna.
5. Progress räknar korrekt över alla uppgifter (Fas 0 inräknad).
6. Allt fungerar på mobil (testat i Chrome DevTools på 375 px bredd).
7. localStorage använder ny nyckel `mba_launch_v2`.
