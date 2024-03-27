# iXBRL voorbeelden

Voor micro, kleine en middelgrote rechtspersonen is elk een template in iXBRL uitgewerkt.
Dit zijn iXBRL versies van de door de NBA verstrekte jaarrekening voorbeelden en zijn gedeeltelijk getagd.
De voorbeelden dienen enkel ter indicatie en derhalve kunnen er geen rechten aan worden ontleend.

Belangrijk: het bestand moet in iXBRL 1.1 formaat worden opgesteld en moet dus voldoen aan de eisen in de [iXBRL 1.1](https://specifications.xbrl.org/work-product-index-inline-xbrl-inline-xbrl-1.1.html) specificatie, waarvan de belangrijkste structuren zijn gebaseerd op de [XHTML 1.0](https://www.w3.org/TR/xhtml1) standaard. 

Met als belangrijkste aandachtspunten:
- tags moeten altijd gesloten worden: `<tag></tag>` of 'self closing': `<tag />`
- de semantische tags uit HTML 5 mogen niet worden gebruikt

## 2.Aanpassen van een template

### 2.1 Standaard pagina layout:

Dit template moet gebruikt worden voor een standaard pagina.

<details>
<summary>Template</summary>

```html
<div class="page">
  <div class="header">
    <div class="header-content"></div>
    <div class="header-line"></div>
  </div>
  <div class="content">
  </div>
  <div class="footer">
    <div class="footer-content"></div>
    <div class="footer-page-number"></div>
  </div>
</div>
```

</details>

### 2.2 Pagina inhoud

De `<div class="content"></div>` moet worden gebruikt voor de inhoud van de pagina, die kan bestaan uit:
- Hoofdstuk- en paragraaftitels: `<h1></h1>` tot `<h6></h6>`; voor titels in de inhoudsopgave gebruik `<span></span>` met `class="toc-h1"` of `class="toc-h2"`
- Paragraaf: `<p></p>`
- Vetgedrukte tekst: `<b></b>`
- Cursieve tekst: `<i></i>`
- <ins>Onderstreepte</ins> tekst: `<u></u>`
- <s>Doorstreepte</s> tekst: `<s></s>`
- [Links](): `<a></a>`
- <q>Inline citaten</q>: `<q></q>`
- Ongeordende lijsten: `<ul></ul>` met geneste `<li></li>`
- Geordende lijsten: `<ol></ol>` met geneste `<li></li>`
  - Cijfers (standaard): `type="1"`
  - Hoofdletters: `type="A"`
  - Kleine letters: `type="a"`
  - Romeinse cijfers in hoofdletters: `type="I"`
  - De lijstitems worden genummerd met Romeinse cijfers in kleine letters: `type="i"`
- Beschrijvingslijsten of definities: `<dl></dl>` met geneste `<dt></dt>` en `<dd></dd>`
- Horizontale lijnen: `<hr />`
- Line break: `<br />` OF gebruik een line break in de tekst
- Tabellen: `<table></table>` met geneste `<tr></tr>` en `<td></td>`
- Afbeeldigen: `<img />`

### 2.3 Titelpagina

Dit template kan gebruikt worden voor de titelpagina
<details><summary>Template</summary>

```html
<div class="page">
  <div class="header">
    <div class="header-content"></div>
    <div class="header-line"></div>
  </div>
  <div class="content">
    <div class="title">
      <div class="title-line"></div>
      <div class="title-content">
        <first-page-title>Voorbeeld rapport 2022</first-page-title>
        <first-page-subtitle>De Middelgrote B.V.</first-page-subtitle>
        <first-page-subtitle>Statutaire vestigingsplaats</first-page-subtitle>
      </div>
    </div>
    <div class="date">
      <div class="date-line"></div>
      <div class="date-content">
        <p>d.d. maand 2024
          Kamer van Koophandel nr. 12345678
          Vastgesteld door de algemene vergadering op 19 maart 2023
        </p>
      </div>
    </div>
  </div>
  <div class="footer">
    <div class="footer-content"></div>
    <div class="footer-page-number"></div>
  </div>
</div>
```

</details>

### 2.4 Header & Footer

De inhoud van de header and footer is opgenomen als CSS in `<style>`

<details><summary>Footer</summary>

```css
.footer-content::after {
  content: "De ...... B.V., Statutaire vestigingsplaats";
}
```
```css
.page:nth-child(n+3) .footer-page-number::after {
  content: "Pagina " counter(page) " van ...";
}
```

</details>
<details><summary>Header</summary>

#### Header:

```css
.header-content::after {
  content: "Samenstellingsverklaring afgegeven d.d. ......";
}
```

</details>

### 2.5 Tabellen

#### 2.5.1 Tabel templates

Voor het gebruik van tabellen zijn een aantal templates beschikbaar (voor het aanpassen van deze templates zie 2.5.2 en 2.5.3):

<details>
<summary>Tabel met 1 kolom</summary>

```html
<table class="table-full">
  <colgroup>
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td>
        <h2>kolom header</h2>
      </td>
    </tr>
    <tr class="empty-row top-table-header">
      <td>
        <hr />
      </td>
    </tr>
  </tbody>
  <tbody>
    <tr class="empty-row">
      <td></td>
    </tr>
    <tr>
      <td>rij</td>
    </tr>
  </tbody>
</table>
```

</details>
<details>
<summary>Tabel met 1 kolom en rij headers</summary>

```html
<table class="table-full col-m">
  <colgroup>
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
    </tr>
    <tr class="empty-row top-table-header">
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
    <tr class="unit-row">
      <td class="scale">(x 1.000)</td>
      <td>€</td>
    </tr>
  </tbody>
  <tbody>
    <tr class="empty-row">
      <td colspan="2"></td>
    </tr>
    <tr>
      <td>
        <h2>rij header</h2>
      </td>
      <td>0</td>
    </tr>
    <tr>
      <td>
        <h3>rij header</h3>
      </td>
      <td>0</td>
    </tr>
    <tr>
      <td>rij header</td>
      <td>0</td>
    </tr>
    <tr class="empty-row sub-total">
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
    <tr>
      <td></td>
      <td>0</td>
    </tr>
    <tr class="empty-row total">
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
  </tbody>
</table>
```

</details>
<details>
<summary>Tabel met 2 kolommen</summary>

```html
<table class="table-full col-xl no-row-headers">
  <colgroup>
    <col />
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td>
        <h2>kolom header</h2>
      </td>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
    </tr>
    <tr class="empty-row top-table-header">
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
  </tbody>
  <tbody>
    <tr class="empty-row">
      <td colspan="3"></td>
    </tr>
    <tr>
      <td>rij</td>
      <td></td>
      <td>0</td>
    </tr>
  </tbody>
</table>
```

</details>
<details>
<summary>Tabel met 2 kolommen en rij headers</summary>

```html
<table class="table-full col-m">
  <colgroup>
    <col />
    <col />
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
    </tr>
    <tr class="empty-row top-table-header">
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
    <tr class="unit-row">
      <td class="scale">(x 1.000)</td>
      <td>€</td>
      <td></td>
      <td>€</td>
    </tr>
  </tbody>
  <tbody>
    <tr class="empty-row">
      <td colspan="4"></td>
    </tr>
    <tr>
      <td>
        <h2>rij header</h2>
      </td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
      <td>
        <h3>rij header</h3>
      </td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr>
      <td>rij header</td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr class="empty-row sub-total">
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
    <tr>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr class="empty-row total">
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
  </tbody>
</table>
```

</details>
<details>
<summary>Tabel met 3 kolommen en rij headers</summary>

```html
<table class="table-full col-m">
  <colgroup>
    <col />
    <col />
    <col />
    <col />
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
    </tr>
    <tr class="empty-row top-table-header">
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
    <tr class="unit-row">
      <td class="scale">(x 1.000)</td>
      <td>€</td>
      <td></td>
      <td>€</td>
      <td></td>
      <td>€</td>
    </tr>
  </tbody>
  <tbody>
    <tr class="empty-row">
      <td colspan="6"></td>
    </tr>
    <tr>
      <td>
        <h2>rij header</h2>
      </td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr>
      <td>
        <h3>rij header</h3>
      </td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr>
      <td>rij header</td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr class="empty-row sub-total">
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
    <tr>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr class="empty-row total">
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
  </tbody>
</table>
```

</details>
<details>
<summary>Tabel met 4 kolommen en rij headers</summary>

```html
<table class="table-full col-m">
  <colgroup>
    <col />
    <col />
    <col />
    <col />
    <col />
    <col />
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
    </tr>
    <tr class="empty-row top-table-header">
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
    <tr class="unit-row">
      <td class="scale">(x 1.000)</td>
      <td>€</td>
      <td></td>
      <td>€</td>
      <td></td>
      <td>€</td>
      <td></td>
      <td>€</td>
    </tr>
  </tbody>
  <tbody>
    <tr class="empty-row">
      <td colspan="8"></td>
    </tr>
    <tr>
      <td>
        <h2>rij header</h2>
      </td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr>
      <td>
        <h3>rij header</h3>
      </td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr>
      <td>rij header</td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr class="empty-row sub-total">
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
    <tr>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr class="empty-row total">
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
  </tbody>
</table>
```

</details>
<details>
<summary>Tabel met 4 gegroepeerde kolommen en rij headers</summary>

```html
<table class="table-full col-s">
        <colgroup>
          <col />
          <col />
          <col />
          <col />
          <col />
          <col />
          <col />
          <col />
        </colgroup>
        <tbody>
          <tr>
            <td></td>
            <td colspan="3">
              <h2>kolom header</h2>
            </td>
            <td></td>
            <td colspan="3">
              <h2>kolom header</h2>
            </td>
          </tr>
          <tr class="empty-row top-table-header">
            <td></td>
            <td colspan="3">
              <hr />
            </td>
            <td></td>
            <td colspan="3">
              <hr />
            </td>
          </tr>
          <tr class="unit-row">
            <td class="scale">(x 1.000)</td>
            <td>€</td>
            <td></td>
            <td>€</td>
            <td></td>
            <td>€</td>
            <td></td>
            <td>€</td>
          </tr>
        </tbody>
        <tbody>
          <tr class="empty-row">
            <td colspan="8"></td>
          </tr>
          <tr>
            <td>
              <h2>rij header</h2>
            </td>
            <td>0</td>
            <td></td>
            <td></td>
            <td></td>
            <td>0</td>
            <td></td>
            <td></td>
          </tr>
          <tr>
            <td>
              <h3>rij header</h3>
            </td>
            <td>0</td>
            <td></td>
            <td></td>
            <td></td>
            <td>0</td>
            <td></td>
            <td></td>
          </tr>
          <tr class="empty-row sub-total">
            <td></td>
            <td>
              <hr />
            </td>
            <td></td>
            <td></td>
            <td></td>
            <td>
              <hr />
            </td>
            <td></td>
            <td></td>
          </tr>
          <tr>
            <td>
              <h2>sub-totaal</h2>
            </td>
            <td></td>
            <td></td>
            <td>0</td>
            <td></td>
            <td></td>
            <td></td>
            <td>0</td>
          </tr>
          <tr class="empty-row sub-total">
            <td></td>
            <td></td>
            <td></td>
            <td>
              <hr />
            </td>
            <td></td>
            <td></td>
            <td></td>
            <td>
              <hr />
            </td>
          </tr>
          <tr>
            <td>
              <h2>totaal</h2>
            </td>
            <td></td>
            <td></td>
            <td>0</td>
            <td></td>
            <td></td>
            <td></td>
            <td>0</td>
          </tr>
          <tr class="empty-row total">
            <td></td>
            <td></td>
            <td></td>
            <td>
              <hr />
            </td>
            <td></td>
            <td></td>
            <td></td>
            <td>
              <hr />
            </td>
          </tr>
        </tbody>
      </table>
```

</details>
<details>
<summary>Tabel met 4 gegroepeerde kolommen, rij headers en referenties</summary>

```html
<table class="table-full col-s annotated">
        <colgroup>
          <col />
          <col />
          <col />
          <col />
          <col />
          <col />
          <col />
          <col />
          <col />
        </colgroup>
        <tbody>
          <tr>
            <td></td>
            <td></td>
            <td colspan="3">
              <h2>kolom header</h2>
            </td>
            <td></td>
            <td colspan="3">
              <h2>kolom header</h2>
            </td>
          </tr>
          <tr class="empty-row top-table-header">
            <td></td>
            <td></td>
            <td colspan="3">
              <hr />
            </td>
            <td></td>
            <td colspan="3">
              <hr />
            </td>
          </tr>
          <tr class="unit-row">
            <td class="scale">(x 1.000)</td>
            <td>Ref.</td>
            <td>€</td>
            <td></td>
            <td>€</td>
            <td></td>
            <td>€</td>
            <td></td>
            <td>€</td>
          </tr>
        </tbody>
        <tbody>
          <tr class="empty-row">
            <td colspan="9"></td>
          </tr>
          <tr>
            <td>
              <h2>rij header</h2>
            </td>
            <td>0.</td>
            <td>0</td>
            <td></td>
            <td></td>
            <td></td>
            <td>0</td>
            <td></td>
            <td></td>
          </tr>
          <tr>
            <td>
              <h3>rij header</h3>
            </td>
            <td>0.</td>
            <td>0</td>
            <td></td>
            <td></td>
            <td></td>
            <td>0</td>
            <td></td>
            <td></td>
          </tr>
          <tr class="empty-row sub-total">
            <td></td>
            <td></td>
            <td>
              <hr />
            </td>
            <td></td>
            <td></td>
            <td></td>
            <td>
              <hr />
            </td>
            <td></td>
            <td></td>
          </tr>
          <tr>
            <td>
              <h2>sub-totaal</h2>
            </td>
            <td></td>
            <td></td>
            <td></td>
            <td>0</td>
            <td></td>
            <td></td>
            <td></td>
            <td>0</td>
          </tr>
          <tr class="empty-row sub-total">
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>
              <hr />
            </td>
            <td></td>
            <td></td>
            <td></td>
            <td>
              <hr />
            </td>
          </tr>
          <tr>
            <td>
              <h2>totaal</h2>
            </td>
            <td></td>
            <td></td>
            <td></td>
            <td>0</td>
            <td></td>
            <td></td>
            <td></td>
            <td>0</td>
          </tr>
          <tr class="empty-row total">
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td>
              <hr />
            </td>
            <td></td>
            <td></td>
            <td></td>
            <td>
              <hr />
            </td>
          </tr>
        </tbody>
      </table>
```

</details>
<details>
<summary>Tabel met 5 kolommen en rij headers</summary>

```html
<table class="table-full col-m">
  <colgroup>
    <col />
    <col />
    <col />
    <col />
    <col />
    <col />
    <col />
    <col />
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
    </tr>
    <tr class="empty-row top-table-header">
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
    <tr class="unit-row">
      <td class="scale">(x 1.000)</td>
      <td>€</td>
      <td></td>
      <td>€</td>
      <td></td>
      <td>€</td>
      <td></td>
      <td>€</td>
      <td></td>
      <td>€</td>
    </tr>
  </tbody>
  <tbody>
    <tr class="empty-row">
      <td colspan="10"></td>
    </tr>
    <tr>
      <td>
        <h2>rij header</h2>
      </td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr>
      <td>
        <h3>rij header</h3>
      </td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr>
      <td>rij header</td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr class="empty-row sub-total">
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
    <tr>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr class="empty-row total">
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
  </tbody>
</table>
```

</details>
<details>
<summary>Tabel met 6 kolommen en rij headers</summary>

```html
<table class="table-full col-s">
  <colgroup>
    <col />
    <col />
    <col />
    <col />
    <col />
    <col />
    <col />
    <col />
    <col />
    <col />
    <col />
    <col />
  </colgroup>
  <tbody>
    <tr>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
      <td></td>
      <td>
        <h2>kolom header</h2>
      </td>
    </tr>
    <tr class="empty-row top-table-header">
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
    <tr class="unit-row">
      <td class="scale">(x 1.000)</td>
      <td>€</td>
      <td></td>
      <td>€</td>
      <td></td>
      <td>€</td>
      <td></td>
      <td>€</td>
      <td></td>
      <td>€</td>
      <td></td>
      <td>€</td>
    </tr>
  </tbody>
  <tbody>
    <tr class="empty-row">
      <td colspan="12"></td>
    </tr>
    <tr>
      <td>
        <h2>rij header</h2>
      </td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr>
      <td>
        <h3>rij header</h3>
      </td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr>
      <td>rij header</td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr class="empty-row sub-total">
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
    <tr>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
      <td></td>
      <td>0</td>
    </tr>
    <tr class="empty-row total">
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
      <td></td>
      <td>
        <hr />
      </td>
    </tr>
  </tbody>
</table>
```

</details>

#### 2.5.2 Generieke tabel opmaak
Alle klassen hieronder gelden voor `<table></table>`.
- Tabel breedte:
  - Tabel breedte 100%: `class="table-full"`
  - Tabel breedte 85%: `class="table-l"`
  - Tabel breedte 70%: `class="table-m"`
  - Tabel breedte 55%: `class="table-s"`
  - Tabel breedte 40%: `class="table-xs"`
- Tabel zonder rij headers: `class="no-row-headers"`
- Tabel met een extra kolom voor b.v. referenties: `class="annotated"`
- Kolom breedte:
  - Kolom breedte 50%: `class="col-4xl"`
  - Kolom breedte 40%: `class="col-3xl"`
  - Kolom breedte 30%: `class="col-2xl"`
  - Kolom breedte 20%: `class="col-xl"`
  - Kolom breedte 17.5%: `class="col-l"`
  - Kolom breedte 15%: `class="col-m"`
  - Kolom breedte 12.5%: `class="col-s"`
  - Kolom breedte 10%: `class="col-xs"`

#### 2.5.3 Styling van de specifieke onderdelen van de tabel

##### Lege regel

`<tr></tr>` met `class="empty-row"`

##### Eerste gedeelte van de tabel

de eerste `<tbody></tbody>` in de tabel is voor de headers en eenheden en bevat
- kolom headers: `<table></table>` met geneste `<h2></h2>`
- kolom header lijn: `<tr></tr>` met `class="top-table-header"`
- eenheden lijn: `<tr></tr>` met `class="unit-row"`
  - als een schaal toegepast is: `<td></td>` met `class="scale"`

##### Tweede gedeelte van de tabel

de tweede `<tbody></tbody>` in de tabel is voor de data en bevat:
- bullet voor header: `<td></td>` met `class="non-list-bullet"`
- subtotaal lijn: `<tr></tr>` met `class="sub-total"` met geneste `<td></td>` en `<hr \>`
- totaal lijn: `<tr></tr>` met `class="total"` met geneste `<td></td>` en `<hr \>`
- stippel lijn: `<tr></tr>` met `class="dotted"` met geneste `<td></td>` en `<hr \>`
- rij headers `<table></table>` met geneste `<h2></h2>` of `<h3></h3>`

#### 2.5.4 Tabel voetnoot

`<p></p>` met `class="footnote-table"` na de tabel