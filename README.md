# projekt1
import sqlite3


db_path = 'magazyn'
conn = sqlite3.connect(db_path)

c = conn.cursor()
#
# Tabele
#
c.execute('''
          CREATE TABLE magazyn
          ( id INTEGER PRIMARY KEY,
            mag_data DATE NOT NULL,
            kategoria VARCHAR(20)
          )
          ''')
c.execute('''
          CREATE TABLE magProdukty
          ( nazwa VARCHAR(100),
            cena NUMERIC NOT NULL,
            ilosc INTEGER NOT NULL,
            mag_id INTEGER,
           FOREIGN KEY(mag_id) REFERENCES magazyn(id),
           PRIMARY KEY (nazwa, mag_id))
          ''')
