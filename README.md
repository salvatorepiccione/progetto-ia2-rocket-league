# Progetto di Intelligenza Artificiale 2: Classificazione di Skillshot in Rocket League

**Autori:**
*   William Carradori (Matricola: 1914036)
*   Salvatore Piccione (Matricola: 2069571)

---

## Descrizione del Progetto

Questo progetto ha l'obiettivo di classificare diverse manovre complesse (*skillshot*) del videogioco *Rocket League*. Partendo da dati di telemetria grezzi, organizzati come serie temporali a lunghezza variabile, abbiamo sviluppato e validato una pipeline di machine learning per predire quale manovra specifica è stata eseguita.

Il lavoro si articola attraverso le seguenti fasi:
1.  **Parsing dei Dati:** Abbiamo scritto uno script per leggere il formato `.data` originale e strutturarlo in un DataFrame `pandas`.
2.  **Feature Engineering:** Abbiamo trasformato le serie temporali in vettori a lunghezza fissa tramite aggregazione di statistiche (media, deviazione standard, mediana, etc.), gestendo in modo differenziato le variabili continue e quelle binarie.
3.  **Selezione del Modello:** Abbiamo confrontato tre diversi classificatori (Regressione Logistica, LDA, KNN) utilizzando una pipeline completa di standardizzazione (`StandardScaler`) e riduzione di dimensionalità (`PCA`). La valutazione è stata fatta tramite cross-validation stratificata, usando l'**F1-score pesato** come metrica principale a causa dello sbilanciamento delle classi.
4.  **Valutazione Finale:** Il modello migliore, la Regressione Logistica, è stato addestrato sull'intero training set e le sue performance sono state misurate sul test set, tenuto isolato per garantire una valutazione imparziale.

## Dataset

Abbiamo utilizzato il dataset **Rocket League Skillshots Data Set**, disponibile pubblicamente sull'UCI Machine Learning Repository.

*   **Fonte:** [Link al Dataset su UCI](https://archive.ics.uci.edu/dataset/858/rocket+league+skillshots)

Il dataset contiene le registrazioni di telemetria di 298 manovre, suddivise in 7 classi (6 skillshot + 1 classe "rumore").

## Librerie Utilizzate

Per eseguire il codice, sono necessarie le seguenti librerie Python:
*   `pandas`
*   `numpy`
*   `matplotlib`
*   `seaborn`
*   `scikit-learn`
*   `gdown` (per lo scaricamento automatico del dataset)

Puoi installare tutte le dipendenze tramite `pip`:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn gdown
```

## Come Riprodurre i Risultati

1.  Assicurati di avere un ambiente Python e le librerie elencate sopra.
2.  Esegui il notebook `IA2_Progetto_Piccione_Carradori_Codice.ipynb` utilizzando un ambiente come Jupyter Notebook, JupyterLab o Google Colab.
3.  Le celle del notebook possono essere eseguite in sequenza dall'inizio alla fine. Il dataset verrà scaricato automaticamente dalla prima cella di codice se non è già presente nella stessa directory.

## Struttura del Repository

*   `README.md`: Questo file, con la descrizione del progetto e le istruzioni.
*   `IA2_Progetto_Piccione_Carradori_Codice.ipynb`: Il notebook Jupyter che contiene tutto il codice, l'analisi e le visualizzazioni.
