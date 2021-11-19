! pip install google_currency
from  tkinter import *
from tkinter import ttk
from tkinter.ttk import Combobox
from google_currency import convert
from tkinter import messagebox
import json
import time as tm
root=Tk()
root.geometry("550x400")
root.title("CURRENCY CONVERTOR")
root.config(bg="black")
root.minsize(550,400)
root.maxsize(550,400)
combostyle = ttk.Style()

combostyle.theme_create('combostyle', parent='alt',
                         settings = {'TCombobox':
                                     {'configure':
                                      {'selectbackground': 'red',
                                       'fieldbackground': 'magenta',
                                       'background': 'green'
                                       }}}
                         )
combostyle.theme_use('combostyle') 
current_time=tm.strftime('%I:%M:%S:%p')
lbl5=Label(root,text=current_time,font=("Charter BT",8,"bold"),bg="black",fg="magenta").place(x=10,y=10)
date=tm.strftime('%d-%b-%Y')
lbl6=Label(root,text=date,font=("Charter BT",8,"bold"),bg="black",fg="magenta").place(x=470,y=10)
def tc():
    messagebox.showinfo("T&C","1.Please do not copy our project.\n2.It take some time to convert.\n3.You have to install a library first to use this program\n4.You must have a good internet connection\n5.All rights reserved to Punit and Neha Sharan")
    

def mainfunction():
    enteramt=fromamt.get()
    convrtamt=tomamt.get()
    var3=convrate[enteramt]
    var4=convrate[convrtamt]
    var5=var.get()
    var6=convert(enteramt,convrtamt,var5)
    var7=json.loads(var6)
    var8=var7["amount"]
    var1.set(var8)
rates=('INR','USD','EUR','CAD','RUB','AUD','CNY','NZD','AFN','ALL','DZD','AOA','XCD','ARS','AMD','AWG','SHP','AZN','BSD','BHD','BDT','BBD','BYN','BZD'
,'XOF','BMD','BTN','BOB','BAM','BWP','BRL','BND','BGN','BIF','CVE','KHR','XAF','KYD','NZD','CLP','COP','KMF','CDF'
,'CRC','HRK','CUP','ANG','CZK','DKK','DJF','DOP','EGP','ERN','SZL','ETB','FKP','FJD','XPF','GMD','GEL','GHS','GIP','GTQ','GGP'
,'GNF','GYD','HTG','HNL','HKD','HUF','ISK','IDR','XDR','IRR','IQD','IMP','ILS','JMD','JPY','JEP','JOD','KZT','KES','KWD','KGS',
'LAK','LBP','LSL','LRD','LYD','CHF','MOP','MGA','MWK','MYR','MVR','MRU','MUR','MXN','MDL','MNT','MAD','MZN','MMK','NAD','NPR'
,'NIO','NGN','KPW','MKD','NOK','OMR','PKR','PGK','PYG','PEN','PHP','PLN','QAR','RON','RWF','WST','STN','SAR','RSD','SCR'
,'SLL','SGD','SBD','SOS','ZAR','GBP','KRW','SSP','LKR','SDG','SRD','SEK','SYP','TWD','TJS','TZS','THB','TOP','TTD','TND','TRY'
,'TMT','UGX','UAH','AED','UYU','UZS','VUV','VES','VND','YER','ZMW')
convrate = {}
for rate in rates:
    firsttype = rate.split("\t")
    convrate[firsttype[0]] = firsttype[0]
        
title=Label(root,text="Currency Convertor",fg="magenta",bg="black",font=("Charter BT",15,"bold")).pack()
amount=Label(root,text="Amount to convert   = ",fg="magenta",bg="black",font=("Charter BT",12,"bold")).place(x=20,y=40)
var=IntVar()
amount1=Entry(root,text=var,bg="magenta",fg="blue",font=("Charter BT",12,"bold")).place(x=200,y=40)
lbl1=Label(root,text="Select the currency to convert From = ",bg="black",fg="magenta",font=("Charter BT",12,"bold")).place(x=20,y=80)
select=StringVar()
fromamt=Combobox(root,text=select,state="readonly")
fromamt['values'] = [currncy for currncy in convrate.keys()]
fromamt.current(0)
fromamt.place(x=310,y=80)
lbl2=Label(root,text="Select the currency to convert into = ",bg="black",fg="magenta",font=("Charter BT",12,"bold")).place(x=20,y=110)
select1=StringVar()
tomamt=Combobox(root,text=select1,state="readonly")
tomamt['values'] = [currncy for currncy in convrate.keys()]
tomamt.current(1)
tomamt.place(x=310,y=110)
lbl8=Label(root,text="If you don't know currency code check here.",bg="black",fg="magenta",font=("Charter BT",8,"bold")).place(x=20,y=150)
check=StringVar()
ccode=Combobox(root,text=check,state="readonly",width=35)
ccode['values'] = (
"Afghanistan = AFN","Akrotiri and Dhekelia (UK) = EUR","Aland Islands (Finland) = EUR","Albania = ALL","Algeria = DZD",
"American Samoa (USA) = USD""Andorra = EUR""Angola = AOA""Anguilla (UK) = XCD""Antigua and Barbuda = XCD",
"Argentina = ARS","Armenia = AMD","Aruba (Netherlands) = AWG","Ascension Island (UK) = SHP","Australia = AUD","Austria = EUR","Azerbaijan = AZN",
"B""Bahamas = BSD","Bahrain = BHD","Bangladesh = BDT","Barbados = BBD","Belarus = BYN",
"Belgium = EUR","Belize = BZD","Benin = XOF","Bermuda (UK) = BMD","Bhutan = BTN","Bolivia = BOB",
"Bonaire (Netherlands) = USD","Bosnia and Herzegovina = BAM","Botswana = BWP","Brazil = BRL","British Indian Ocean Territory (UK) = USD",
"British Virgin Islands (UK) = USD","Brunei = BND","Bulgaria = BGN","Burkina Faso = XOF","Burundi = BIF",
"C","Cabo Verde = CVE","Cambodia = KHR","Cameroon = XAF","Canada = CAD","Caribbean Netherlands (Netherlands) = USD",
"Cayman Islands (UK) = KYD","Central African Republic = XAF","Chad = XAF","Chatham Islands (New Zealand) = NZD","Chile = CLP","China = CNY",
"Christmas Island (Australia) = AUD","Cocos (Keeling) Islands (Australia) = AUD","Colombia = COP","Comoros = KMF",
"Congo, Democratic Republic of the = CDF","Congo, Republic of the = XAF","Cook Islands (New Zealand) = none","Costa Rica = CRC","Cote d'Ivoire = XOF",
"Croatia = HRK","Cuba = CUP","Curacao (Netherlands) = ANG","Cyprus = EUR","Czechia = CZK",
"D","Denmark = DKK","Djibouti = DJF","Dominica = XCD","Dominican Republic = DOP",
"E","Ecuador = USD","Egypt = EGP","El Salvador = USD","Equatorial Guinea = XAF","Eritrea = ERN","Estonia = EUR","Eswatini = SZL","Ethiopia = ETB",
"F","Falkland Islands (UK) = FKP","Faroe Islands (Denmark) = none","Fiji = FJD","Finland = EUR",
"France = EUR","French Guiana (France) = EUR","French Polynesia (France) = XPF",
"G","Gabon = XAF","Gambia = GMD","Georgia = GEL","Germany = EUR","Ghana = GHS","Gibraltar (UK) = GIP",
"Greece = EUR","Greenland (Denmark) = DKK","Grenada = XCD","Guadeloupe (France) = EUR","Guam (USA) = USD","Guatemala = GTQ",
"Guernsey (UK) = GGP","Guinea = GNF","Guinea-Bissau = XOF",
"Guyana = GYD",
"H","Haiti = HTG","Honduras = HNL","Hong Kong (China) = HKD","Hungary = HUF",
"I","Iceland = ISK","India = INR","Indonesia = IDR","International Monetary Fund (IMF) = XDR","Iran = IRR",
"Iraq = IQD","Ireland = EUR","Isle of Man (UK) = IMP","Israel = ILS","Italy = EUR",
"J""Jamaica = JMD""Japan = JPY""Jersey (UK) = JEP""Jordan = JOD",
"K","Kazakhstan = KZT","Kenya = KES","Kiribati = AUD","Kosovo = EUR","Kuwait = KWD","Kyrgyzstan = KGS",
"L","Laos = LAK","Latvia = EUR","Lebanon = LBP","Lesotho = LSL","Liberia = LRD","Libya = LYD","Liechtenstein = CHF","Lithuania = EUR","Luxembourg = EUR",
"M","Macau (China) = MOP","Madagascar = MGA","Malawi = MWK","Malaysia = MYR","Maldives = MVR","Mali = XOF",
"Malta = EUR","Marshall Islands = USD","Martinique (France) = EUR","Mauritania = MRU","Mauritius = MUR","Mayotte (France) = EUR",
"Mexico = MXN","Micronesia = USD","Moldova = MDL","Monaco = EUR","Mongolia = MNT","Montenegro = EUR",
"Montserrat (UK) = XCD","Morocco = MAD","Mozambique = MZN","Myanmar = MMK",
"N","Namibia = NAD","Nauru = AUD","Nepal = NPR","Netherlands = EUR","New Caledonia (France) = XPF",
"New Zealand = NZD","Nicaragua = NIO","Niger = XOF","Nigeria = NGN","Niue (New Zealand) = NZD","Norfolk Island (Australia) = AUD",
"Northern Mariana Islands (USA) = USD","North Korea = KPW","North Macedonia = MKD","Norway = NOK",
"O","Oman = OMR",
"P","Pakistan = PKR","Palau = USD","Palestine = ILS","Panama = USD","Papua New Guinea = PGK",
"Paraguay = PYG","Peru = PEN","Philippines = PHP","Pitcairn Islands (UK) = NZD","Poland = PLN","Portugal = EUR","Puerto Rico (USA) = USD",
"Q","Qatar = QAR",
"R","Reunion (France) = EUR","Romania = RON","Russia = RUB","Rwanda = RWF",
"S","Saba (Netherlands) = USD","Saint Barthelemy (France) = EUR","Saint Helena (UK) = SHP","Saint Kitts and Nevis = XCD","Saint Lucia = XCD",
"Saint Martin (France) = EUR","Saint Pierre and Miquelon (France) = EUR","Saint Vincent and the Grenadines = XCD","Samoa = WST","San Marino = EUR","Sao Tome and Principe = STN",
"Saudi Arabia = SAR","Senegal = XOF","Serbia = RSD","Seychelles = SCR","Sierra Leone = SLL","Singapore = SGD",
"Sint Eustatius (Netherlands) = USD","Sint Maarten (Netherlands) = ANG","Slovakia = EUR","Slovenia = EUR","Solomon Islands = SBD","Somalia = SOS",
"South Africa = ZAR","South Georgia Island (UK) = GBP","South Korea = KRW","South Sudan = SSP","Spain = EUR","Sri Lanka = LKR","Sudan = SDG",
"Suriname = SRD","Svalbard and Jan Mayen (Norway) = NOK","Sweden = SEK","Switzerland = CHF","Syria = SYP",
"T","Taiwan = TWD","Tajikistan = TJS","Tanzania = TZS","Thailand = THB","Timor-Leste = USD","Togo = XOF",
"Tokelau (New Zealand) = NZD","Tonga = TOP","Trinidad and Tobago = TTD","Tristan da Cunha (UK) = GBP","Tunisia = TND","Turkey = TRY",
"Turkmenistan = TMT","Turks and Caicos Islands (UK) = USD","Tuvalu = AUD",
"U","Uganda = UGX","Ukraine = UAH","United Arab Emirates = AED","United Kingdom = GBP","United States of America = USD","Uruguay = UYU",
"US Virgin Islands (USA) = USD","Uzbekistan = UZS",
"V","Vanuatu = VUV","Vatican City (Holy See) = EUR","Venezuela = VES","Vietnam = VND",
"W","Wake Island (USA) = USD","Wallis and Futuna (France) = XPF",
"Y","Yemen = YER",
"Z","Zambia = ZMW","Zimbabwe = USD",
)
ccode.current(0)
ccode.place(x=20,y=170)
var1=IntVar()
convertbtn=Button(root,bg="red",fg="black",text="Convert",command=mainfunction).place(x=255,y=170)
lbl3=Label(root,text="Converted Amount = ",bg="black",fg="magenta",font=("Charter BT",16,"bold")).place(x=80,y=250)
convertamt=Entry(root,bg="magenta",fg="blue",text=var1,font=("Charter BT",12,"bold"),state="readonly").place(x=300,y=255)
lbl4=Label(root,text="Made by Punit And Neha Sharan",bg="black",fg="magenta",font=("Charter BT",8,"bold")).place(x=200,y=380)
lbl4=Button(root,text="T&C",bg="black",fg="magenta",font=("Charter BT",8,"bold"),command=tc).place(x=520,y=380)
root.mainloop()
