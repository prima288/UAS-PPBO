// Class untuk mewakili tiket
class Ticket {
    private String destination;
    private double price;
    private boolean isBooked;

    public Ticket(String destination, double price) {
        this.destination = destination;
        this.price = price;
        this.isBooked = false;
    }

    public String getDestination() {
        return destination;
    }

    public double getPrice() {
        return price;
    }

    public boolean isBooked() {
        return isBooked;
    }

    public void bookTicket() {
        isBooked = true;
    }

    public void cancelBooking() {
        isBooked = false;
    }

    // Method override toString() untuk mencetak informasi tiket
    @Override
    public String toString() {
        return "Destinasi: " + destination + "\nHarga: " + price + "\nStatus Pemesanan: " + (isBooked ? "Terpesan" : "Belum Dipesan") + "\n";
    }
}

// Class turunan untuk mewakili tiket pesawat
class FlightTicket extends Ticket {
    private String airline;

    public FlightTicket(String destination, double price, String airline) {
        super(destination, price);
        this.airline = airline;
    }

    public String getAirline() {
        return airline;
    }

    // Method override toString() untuk mencetak informasi tiket pesawat
    @Override
    public String toString() {
        return super.toString() + "Maskapai: " + airline + "\n";
    }
}

// Class untuk mewakili sistem pemesanan tiket
class TicketingSystem {
    private Ticket[] tickets;

    public TicketingSystem(int capacity) {
        tickets = new Ticket[capacity];
    }

    public void addTicket(Ticket ticket, int index) {
        tickets[index] = ticket;
    }

    public Ticket[] getTickets() {
        return tickets;
    }

    public Ticket bookTicket(int index) {
        Ticket ticket = tickets[index];
        if (!ticket.isBooked()) {
            ticket.bookTicket();
            return ticket;
        } else {
            return null; // Jika tiket sudah dipesan
        }
    }

    public void cancelBooking(int index) {
        tickets[index].cancelBooking();
    }
}

public class Main {
    public static void main(String[] args) {
        // Membuat objek tiket
        Ticket ticket1 = new Ticket("Jakarta", 100.0);
        Ticket ticket2 = new FlightTicket("Bandung", 50.0, "Garuda Indonesia");

        // Membuat objek sistem pemesanan tiket
        TicketingSystem ticketingSystem = new TicketingSystem(2);

        // Menambahkan tiket ke sistem
        ticketingSystem.addTicket(ticket1, 0);
        ticketingSystem.addTicket(ticket2, 1);

        // Mencetak semua tiket dalam sistem menggunakan anonymous class
        System.out.println("Daftar Tiket:");
        for (Ticket ticket : ticketingSystem.getTickets()) {
            System.out.println(ticket.toString());
        }

        // Memesan tiket
        int bookedTicketIndex = 0;
        Ticket bookedTicket = ticketingSystem.bookTicket(bookedTicketIndex);
        if (bookedTicket != null) {
            System.out.println("Tiket dengan destinasi " + bookedTicket.getDestination() + " berhasil dipesan.");
        } else {
            System.out.println("Tiket dengan destinasi " + ticketingSystem.getTickets()[bookedTicketIndex].getDestination() + " sudah dipesan.");
        }

        // Membatalkan pemesanan tiket
        int canceledTicketIndex = 1;
        ticketingSystem.cancelBooking(canceledTicketIndex);
        System.out.println("Pemesanan tiket dengan destinasi " + ticketingSystem.getTickets()[canceledTicketIndex].getDestination() + " berhasil dibatalkan.");

        // Mencetak semua tiket dalam sistem setelah perubahan
        System.out.println("Daftar Tiket setelah Perubahan:");
        for (Ticket ticket : ticketingSystem.getTickets()) {
            System.out.println(ticket.toString());
        }

        // Menggunakan try-catch untuk menangani exception
        try {
            // Mencoba membatalkan pemesanan tiket yang tidak ada (index out of bounds)
            int invalidTicketIndex = 2;
            ticketingSystem.cancelBooking(invalidTicketIndex);
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Terjadi kesalahan: " + e.getMessage());
        }

        // Menggunakan custom annotation
        @Deprecated
        double ticketPrice = ticket1.getPrice();
        System.out.println("Harga tiket: " + ticketPrice);
    }
}
