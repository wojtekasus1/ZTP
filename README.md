# Lifetime Monitor

**Mini klon Downdetectora** – aplikacja do monitorowania dostępności wybranych stron internetowych oraz zgłaszania awarii przez użytkowników.

Projekt prezentuje aktualny status stron, procent ich dostępności w czasie oraz pozwala użytkownikom zgłaszać problemy z działaniem serwisów.

---

## Temat pracy

Celem projektu jest stworzenie uproszczonego systemu monitorowania dostępności stron internetowych, inspirowanego działaniem serwisu Downdetector. Aplikacja cyklicznie sprawdza status wybranych stron zapisanych w bazie danych, oblicza ich procentowy czas dostępności (*uptime*) oraz umożliwia użytkownikom zgłaszanie awarii.

Dzięki połączeniu automatycznych testów dostępności i zgłoszeń od użytkowników możliwe jest uzyskanie bardziej realistycznego obrazu stanu działania monitorowanych serwisów.

---

## Używane technologie

- **Python** 3.10+
- **Flask** – framework webowy
- **SQLite** – baza danych
- **APScheduler** – wykonywanie cyklicznych sprawdzeń
- **Requests** – wysyłanie zapytań HTTP do monitorowanych stron
- **HTML + Bootstrap 5** – warstwa prezentacji

---

## Sposób realizacji

Projekt został zrealizowany przy użyciu frameworka Flask z podziałem na:
- warstwę logiki aplikacji,
- warstwę danych opartą o SQLite,
- warstwę prezentacji opartą o HTML i Bootstrap.

### 1. Wstępnie zdefiniowana lista stron
Monitorowane strony internetowe są wcześniej zapisane w bazie danych. Użytkownik nie dodaje nowych adresów URL, a jedynie przegląda dostępne serwisy i ich status.

### 2. Automatyczne sprawdzanie dostępności
Aplikacja w określonych odstępach czasu wysyła zapytania HTTP do każdej zapisanej strony. Na podstawie odpowiedzi serwera określany jest jej aktualny status:
- **online** – gdy strona odpowiada poprawnie,
- **offline** – gdy strona nie odpowiada lub zwraca błąd.

Wyniki sprawdzeń są zapisywane w bazie danych wraz z czasem wykonania testu.

### 3. Obliczanie procentu uptime
Na podstawie historii automatycznych pomiarów system oblicza procent czasu, w którym dana strona była dostępna. Dzięki temu użytkownik może zobaczyć, jak stabilnie działa dany serwis w dłuższym okresie.

### 4. Zgłaszanie awarii przez użytkowników
Użytkownik może zgłosić problem z działaniem wybranej strony, podobnie jak w serwisie Downdetector. Zgłoszenia są zapisywane w bazie danych i mogą być prezentowane jako dodatkowa informacja o możliwych problemach technicznych.

### 5. Prezentacja wyników
Aplikacja wyświetla:
- nazwę strony,
- aktualny status,
- procent uptime,
- historię ostatnich sprawdzeń,
- liczbę zgłoszeń awarii od użytkowników.

---

## Główne funkcjonalności

- podgląd statusu monitorowanych stron,
- automatyczne sprawdzanie dostępności,
- obliczanie procentowego uptime,
- zgłaszanie awarii przez użytkowników,
- prezentacja historii działania serwisów.

---

## Uruchomienie projektu

### Wymagania
- Python 3.10 lub nowszy

### Instalacja

```bash
git clone https://github.com/wojtekasus1/ZTP
cd lifetime-monitor

python -m venv venv
venv\Scripts\activate
#source venv/bin/activate   #Linux / Mac

pip install -r requirements.txt
python run.py
