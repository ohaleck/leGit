# Problemy obecnego systemu
1. Teksty prawne (ustawy, rozporządzenia, uchwały, zarządzenia itp.) posiadające poprawki nie pozwalają na łatwe otrzymanie obowiązującego (ujednoliconego tekstu). Tekst jednolity powstaje jedynie od czasu do czasu. Powstałe od tego czasu poprawki trzeba samemu nań nanosić by otrzymać obowiązującą wersję dokumentu.
2. Większość dokumentów w BIP umieszczanych jest w plikach PDF lub Office (doc, docx, xls, xlsx itp.). 
    * Nie są to formaty przeznaczone do publikowania treści (PDF służy do przygotowania do druku, Office do edycji)
    * Formaty te są trudne do przeszukiwania
    * Tekst z tych dokumentów ciężko jest skopiować w celu obróbki i ponownego wykorzystania
3. Z powyższych względów technicznych odnalezienie i praca z tekstami aktów prawnych jest bardzo trudna. 
4. Jeszcze gorzej sprawa się ma, gdy dokumenty w BIPie to skany - potrzebny jest w pełni elektroniczny system obiegu dokumentów!! 
5. Obecny system w żaden sposób nie wspomaga prac legislacyjnych, funkcjonuje niejako obok nich


# Założenia
- oddzielenie treści od warstwy prezentacji, wykorzystanie formatu zapisu nie zawierającego informacji o wyglądzie (formatowaniu, foncie, itp.) dokumentu, a jedynie o jego treści i strukturze (paragrafy, punkty, akapity, nagłówki, odnośniki)
- legislatorzy pracują **zawsze** nad pełnym dokumentem, a nie nad opisem zmian
- system zapewnia możliwość wyświetlenia wersji dokumentu z dowolnego momentu w czasie
- system pozwala na wygenerowanie dokumentu w dowolnej formie (PDF, HTML)

# Opis studium (Proof of Concept)
* systemy informatyczne wykonywane w ramach zamówień publicznych najczęściej pisane są od zera. To pozwala na zwiększenie kosztu (zyskuje dostawca rozwiązań, traci podatnik). Tymczasem, tu nie trzeba odkrywać koła na nowo! Wszystkie rozwiązania istnieją, wystarczy je zintegrować w sensowny sposób. 
* zero linii własnego kodu, wykorzystanie istniejącego, darmowego oprogramowania:
    * Git na serwerze GitHub - darmowy dla projektów open source www.github.com
    * język opisu dokumentów MarkDown - otwarty, lekki i czytelny, zarówno dla człowieka, jak i programu (tekst otwarty w Notatniku strukturą przypomina docelowy, sformatowany dokument) http://pl.wikipedia.org/wiki/Markdown
    * edytor tekstowy typu Notatnik
* tekst uchwał został przekopiowany z plików PDF, pozbawiony śmieci (np. nagłówków i stopek), a następnie ręcznie poprawiono formatowanie
* ze względu na pewne niedostatki języka MarkDown (wymuszona, automatyczna numeracja), punkt dodany w §2 ma numer 8, a nie 7a

## Instrukcja obsługi
Baza danycg znajduje się pod adresem: https://github.com/ohaleck/leGit/ i zawiera jedną uchwałę (w strukturze katalogów odpowiadającej numeracji uchwał) i dwie nowelizację. Bazą do pracy jest zawsze tekst ujednolicony, a tekst nowelizacji można wygenerować na ich podstawie (a nie tak, jak obecnie: by otrzymać tekst ujednolicony należy wziąć tekst początkowy i zaaplikować do niego nowelicje). W związku z tym, zawsze dostępny jest najbardziej aktualna wersja tekstu ujednoliconego uchwały:
https://github.com/ohaleck/leGit/blob/master/2011/21/275.md

Przyciskiem ‘Raw’ możemy wyświetlić dokument bez formatowania, w formie takiej, w jakiej jest zapisany czyli w języku Markdown. Jak widać, również jest czytelny (czego nie można powiedzieć o dokumentach w XMLu): https://raw.githubusercontent.com/ohaleck/leGit/master/2011/21/275.md

Pod przyciskiem ‘history’ znajdziemy całą historię zmian dokumentu, w tym dwie poprawki. Klikając na tytuł wersji (np. `UCHWAŁA … w sprawie zmiany uchwały`) przywołujemy przywołujemy treść nowelizacji w formie różnicy między tekstem oryginalnym, a zmienionym - widać wstawione, usunięte i zmienione fragmenty - jest to również bardzo czytelne. Np.: https://github.com/ohaleck/leGit/commit/96cbd6aa2673f5ec32380ea26e83d817649e2b0c

Przycisk ‘<>’ na liście wersji pozwala na wyświetlenie tekstu ujednoliconego uchwały w danej wersji, np. https://github.com/ohaleck/leGit/blob/3520888b89d2fe2c137f3eef520cc2c1cabe1e6b/2011/21/275.md

Wszystkie zmiany są opisane z datą, godziną i autorem. System pozwala również na jednoczesną pracę wielu osób nad tym samym tekstem, tworzenie zespołów i komisji, ustalanie uprawnień (np. zespół proponuje poprawki, jednak wprowadzić je może tylko Przewodniczący RMK) itp. 



# Opis rozwiązania docelowego
## Różnice w stosunku do studium:
* "aktywna" numeracja pozwalająca na adresowanie elementów dokumentu, tworzenie odnośników do nich i opis zmian np. ‘par. 1 ust. 2 otrzymuje brzmienie: … `
* data uchwalenia, data wejścia w życie, numery itp. przechowywane w formie metadanych, co pozwala na automatyzację ich użycia (np. stan obowiązujący na dzień X, opis odnoszący się do numerów artykułów, paragrafów itp., a nie numerów wierszy)
* system uprawnień oparty na kontach i podpisach elektronicznych, jednoczesna praca wielu osób (zespołów) nad jednym dokumentem, jednak jego ostateczne zatwierdzenie wymaga głosowania
## Technologie możliwe do wykorzystania:
* **Git**, otwarty system zarządzania wersjami, wykorzystywany przez największe firmy informatyczne i projekty open source, min. Google, Facebook, Twitter, Microsoft, Linux, Android, Eclipse, PostgreSQLg. 2 lata temu pewien niemiecki informatych umieścił w bazie Git prowadzonej przez GitHub pełen zapis niemieckiego prawa federalnego: https://github.com/bundestag/gesetze
* **MultiMarkdown** lekki, otwarty język opisu dokumentów, oparty na języku Markdown, jednak posiadający dodatkowe funkcje, takie jak odnośniki, tabele, metadane, formatowanie obrazków, itp. http://fletcherpenney.net/multimarkdown/, z możliwymi modyfikacjami, lub:
* zestaw rozwiązań bazujących na XML dla aktów prawnych przez MG: http://prawo.vagla.pl/node/9879
