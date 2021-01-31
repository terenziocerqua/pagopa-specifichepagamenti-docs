Pagamento multi beneficiario
============================

E' possibile che per talune posizioni debitorie la somma totale del debito debba essere ripartita tra più Enti Creditori (tutti aderenti alla piattaforma pagoPA).

In tali casi la stessa posizione debitoria dovrà essere scomposta in diverse RPT ognuna delle quali afferente ad un Ente Creditore coinvolto, tenendo conto delle seguenti osservazioni:

* la prima RPT dell'elenco dovrà essere riferita all'EC che sta inizializzando il carrello.
* ogni RPT dovrà contenere la descrizione della quota parte di pagamento del singolo EC.
* ogni RPT contiene i conti di accredito intestati all'EC a cui è riferita l'RPT.

Le ricevute di tale pagamento saranno consegnate:

* alla stazione dalla quale è partita la richiesta di pagamento
* a tutte le stazioni degli EC coinvolti e dedite alla ricezione di pagamento per conto terzi (parametro della stazione broadcast)
'[TBD alle stazioni degli EC coinvolti se direttamente connessi, alle stazioni degli intermediari se uno o più d'uno degli EC coinvolti non sono direttamente connessi]'

**Esempio**

Il pagamento di un tributo TARI/TEFA pari ad un totale di 110 EUR. In tale scenario il Comune (codice fiscale 777777777) dovrà istruire un pagamento per l'accredito del contributo TARI (100 EUR) verso lo stesso comune, ed il contributo TEFA (10 EUR) verso la sua Provincia di competenza (codice fiscale 999999999).

Il carrello dovrà essere composto da due RPT così composte:

`RPT 1`

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<RPT xmlns="http://www.digitpa.gov.it/schemas/2011/Pagamenti/">
  <versioneOggetto>6.2.0</versioneOggetto>
  <dominio>
    <identificativoDominio>77777777777</identificativoDominio>
  </dominio>
  <identificativoMessaggioRichiesta>...</identificativoMessaggioRichiesta>
  <dataOraMessaggioRichiesta>...</dataOraMessaggioRichiesta>
  <autenticazioneSoggetto>...</autenticazioneSoggetto>
  <soggettoVersante> ... </soggettoVersante>
  <soggettoPagatore>... </soggettoPagatore>
  <enteBeneficiario>
    <identificativoUnivocoBeneficiario>
      <tipoIdentificativoUnivoco>G</tipoIdentificativoUnivoco>
      <codiceIdentificativoUnivoco>77777777777</codiceIdentificativoUnivoco>
    </identificativoUnivocoBeneficiario>
    <denominazioneBeneficiario>Comune</denominazioneBeneficiario>
    <indirizzoBeneficiario>....</indirizzoBeneficiario>
    <civicoBeneficiario>..</civicoBeneficiario>
    <capBeneficiario>...</capBeneficiario>
    <localitaBeneficiario>...</localitaBeneficiario>
    <provinciaBeneficiario>...</provinciaBeneficiario>
    <nazioneBeneficiario>...</nazioneBeneficiario>
  </enteBeneficiario>
  <datiVersamento>
    <dataEsecuzionePagamento>...</dataEsecuzionePagamento>
    <importoTotaleDaVersare>100.00</importoTotaleDaVersare>
    <tipoVersamento>BBT</tipoVersamento>
    <identificativoUnivocoVersamento>...</identificativoUnivocoVersamento>
    <codiceContestoPagamento>...</codiceContestoPagamento>
    <ibanAddebito>...</ibanAddebito>
    <firmaRicevuta>0</firmaRicevuta>
    <datiSingoloVersamento>
      <importoSingoloVersamento>100.00</importoSingoloVersamento>
      <ibanAccredito>...</ibanAccredito>
      <ibanAppoggio>...</ibanAppoggio>
      <credenzialiPagatore>n/a</credenzialiPagatore>
      <causaleVersamento>...</causaleVersamento>
      <datiSpecificiRiscossione>...</datiSpecificiRiscossione>
    </datiSingoloVersamento>
  </datiVersamento>
</RPT>

```

`RPT 2`

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<RPT xmlns="http://www.digitpa.gov.it/schemas/2011/Pagamenti/">
  <versioneOggetto>6.2.0</versioneOggetto>
  <dominio>
    <identificativoDominio>77777777777</identificativoDominio>
  </dominio>
  <identificativoMessaggioRichiesta>...</identificativoMessaggioRichiesta>
  <dataOraMessaggioRichiesta>...</dataOraMessaggioRichiesta>
  <autenticazioneSoggetto>...</autenticazioneSoggetto>
  <soggettoVersante> ... </soggettoVersante>
  <soggettoPagatore>... </soggettoPagatore>
  <enteBeneficiario>
    <identificativoUnivocoBeneficiario>
      <tipoIdentificativoUnivoco>G</tipoIdentificativoUnivoco>
      <codiceIdentificativoUnivoco>999999999</codiceIdentificativoUnivoco>
    </identificativoUnivocoBeneficiario>
    <denominazioneBeneficiario>Provincia</denominazioneBeneficiario>
    <indirizzoBeneficiario>....</indirizzoBeneficiario>
    <civicoBeneficiario>..</civicoBeneficiario>
    <capBeneficiario>...</capBeneficiario>
    <localitaBeneficiario>...</localitaBeneficiario>
    <provinciaBeneficiario>...</provinciaBeneficiario>
    <nazioneBeneficiario>...</nazioneBeneficiario>
  </enteBeneficiario>
  <datiVersamento>
    <dataEsecuzionePagamento>...</dataEsecuzionePagamento>
    <importoTotaleDaVersare>10.00</importoTotaleDaVersare>
    <tipoVersamento>BBT</tipoVersamento>
    <identificativoUnivocoVersamento>...</identificativoUnivocoVersamento>
    <codiceContestoPagamento>...</codiceContestoPagamento>
    <ibanAddebito>...</ibanAddebito>
    <firmaRicevuta>0</firmaRicevuta>
    <datiSingoloVersamento>
      <importoSingoloVersamento>10.00</importoSingoloVersamento>
      <ibanAccredito>...</ibanAccredito>
      <ibanAppoggio>...</ibanAppoggio>
      <credenzialiPagatore>n/a</credenzialiPagatore>
      <causaleVersamento>...</causaleVersamento>
      <datiSpecificiRiscossione>...</datiSpecificiRiscossione>
    </datiSingoloVersamento>
  </datiVersamento>
</RPT>
```
